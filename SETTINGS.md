# Game settings & ini options

The same for every version of the games. Set these in the game’s own menus.

## Required game settings

- **Video**: V-Sync off, frame rate unlocked, motion blur off.  
  TAA / FXAA / DLSS / FSR / Frame Generation / XeSS / CAS / etc. off.  
  Any other video enhancement besides MSAA (FH4/FH5) is unsupported. Use the mod’s own TAA or DLSS/FSR.
- **HDR off** (FH5 and FH6; FH4 has no HDR setting):  
  Settings → Video → HDR, or turn HDR off in Windows (Settings → Display → Use HDR, or Win+Alt+B).  
  With HDR on, the Meta/Quest runtime cannot take the picture and VR stays off for that run. The status window and log will say so.
- **HUD and gameplay**: set the HUD Safe Frame sliders to the stock position for that game. The cockpit elements are made for it; any other value makes them come out cut off or empty.

| Game | HUD Safe Frame Horizontal | HUD Safe Frame Vertical |
|---|---|---|
| Forza Horizon 4 | 8 | 37 |

Forza Horizon 5 and Forza Horizon 6 use their own stock positions. Leave those sliders where the game shipped them. Do not copy the Horizon 4 numbers.

- **Data Out**: ON, IP address `127.0.0.1`, port `20440`.  
  Required for per-car HUD layouts. The seat position usually still works without it. If Data Out already goes to SimHub or a rig, see [Data Out](HUD-AND-SEAT.md#data-out).
- Keep Environment Geometry and Environment Texture high (Extreme if the system can handle it). Lowering them causes late pop-in of cones, barriers, and roadside objects.
- **FH6 only**: Settings → HUD and gameplay → Radar position: Center right. The radar element is made for that position.

You never need to edit the game’s own settings file. The mod writes the render size it needs before the game reads it.

## GrayHorizon Settings app

`GrayHorizon Settings.exe` is included in every zip.  
It shows live status while the game is running, lets you change most options without editing the ini by hand, and checks for updates on GitHub. The mod opens it when the game starts. Turn that off with “Open this window when the game starts”, or `console=0`.

**VR** unticked: the game plays on the monitor as normal (no VR, no hotkeys, no status window), for when someone else plays. At the next start the resolution goes back to the monitor’s if it is still the headset size. Data Out is still passed on. **Start VR by itself** unticked (`auto_start=0`): VR comes on only when you press F8.

Changes apply the next time the game starts. **Use the suggested size** fills in the resolution the performance summary worked out.

![GrayHorizon Settings window with live status](media/settings.png)

Hotkeys (editable on the right side of the window):
- F12 (or a wheel/pad button) — in-headset menu
- F5 — frame-rate readout
- F6 — performance summary (last 30 seconds)
- Ctrl+Space — recenter

The full list is under [Hotkeys](#hotkeys). Wheel and button-box buttons are there too.

## Key ini options

The ini lives next to the game (Steam) or in `Documents\GrayHorizon\FH5` / `FH6` (Game Pass).

| Setting | Values | Notes |
|---------|--------|-------|
| `resolution` | `auto`, `WIDTHxHEIGHT`, `off` | `auto` uses the per-headset table. Recommended. |
| `upscale` | `dlss`, `fsr` (FH4), `off` | DLSS on NVIDIA RTX. FH4 falls back to FSR on other cards. |
| `upscale_scale` | 0.5–1.0 | 0.67 quality, 0.58 balanced, 0.5 performance. 1.0 = AA only. |
| `anti_aliasing` | 0 or 1 | Mod’s own temporal AA when not using an upscaler. |
| `per_eye` / `canted` | see TECHNICAL.md | Canted per-eye is the recommended mode. |
| `trim_top` / `trim_bottom` | 0–40 | Percent of height not drawn (canted mode). Start at 0. |
| `afr_warp` | 0 or 1 | Eye timing warp. On by default. Costs a little GPU. |
| `detail_fov` | `auto`, number, 0 | Controls how far the game draws detailed models. |
| `update_check` | 0 or 1 | Whether Settings looks for updates on launch. |

Per-headset sizes go under `[resolutions_canted]` (or `[resolutions]`).  
Example:

```ini
[resolutions_canted]
L67_R45_U57_D57=4504x5984
```

`[resolutions_canted]` is used in canted mode, `[resolutions]` otherwise. One line per headset, so a headset with swappable lens modules keeps a size for each. The size is the untrimmed picture, rounded to a multiple of 8. A module the mod has already seen in VR is recognised at launch.

Each headset can also keep its own render scale, trim and foveated level. GrayHorizon Settings has a **Headset** list at the top: pick one, give it a name, and the size, scale, foveated level and trim below it belong to that headset. In the ini it is a section named after the field of view. A value that is missing there is taken from `[settings]`.

```ini
[headset_L67_R45_U57_D57]
name=Pimax Crystal Super Ultrawide
upscale_scale=0.67
trim_top=25
trim_bottom=30
foveated=1
```

85% and 75% are not DLSS presets. Put them in that headset’s section as `upscale_scale=0.85` or `0.75`.

A few more on upscaling:

- `upscale_sharpness` (0 to 1) sharpens after DLSS. `taa_sharpness` (0 to 1) does the same for the mod’s own temporal AA.
- `dlss_preset=auto` picks the model for your card. A letter forces one.
- FSR (FH4 only) runs on any DirectX 12 GPU. It is not as clean as DLSS: thin lines shimmer a little. It is chosen by itself when `upscale=dlss` meets a card that is not an RTX.
- With an upscaler, turn the game’s MSAA off.
- DLSS costs time based on the size it **outputs**, not the size the game renders. If the GPU is the limit, a smaller resolution helps more than a lower `upscale_scale`. A lower percentage often looks better, so try that first (see [PERFORMANCE.md](PERFORMANCE.md)).

## Hotkeys

They work while the game window has focus. Change them in GrayHorizon Settings or under `[hotkeys]` in the ini. The Horizon games do not use the function keys themselves.

| Default | Name | Action |
|---|---|---|
| F12 | `menu` | In-headset menu |
| F8 | `vr_toggle` | VR on / off |
| Ctrl+Space | `recenter` | Recenter |
| Ctrl+Up / Ctrl+Down | `seat_forward` / `seat_back` | Seat forward / back 1 cm |
| Ctrl+PgUp / Ctrl+PgDn | `seat_up` / `seat_down` | Seat up / down 1 cm |
| F11 | `panels` | Speedometer element off / on until the game is closed |
| F5 | `fps` | Frame-rate readout in the headset |
| F6 | `performance` | Performance display (last 30 seconds) |
| F9 | `console` | Status window show / hide |
| Ctrl+Shift+F11 | `per_eye` | Per-eye rendering on / off (FH4 only) |
| F3 | `screenshot` | What you see in the headset, HUD included. A JPEG in `Pictures\GrayHorizon`. The flat screen while in a menu. |
| F4 | `frame_capture` | Capture for a problem report. Large files in the game folder. |

**In the menu since 1.1, and no longer a hotkey:** flat view, HUD calibration, save the HUD as the default, stable camera, eye timing warp, anti-aliasing, sharpening and foveated rendering. A binding for one of those left in an older ini is ignored, and the log says so.

Write a key on its own or with `Ctrl`, `Shift` and/or `Alt` (`F1`–`F24`, `A`–`Z`, `0`–`9`, `Space`, `Up`, `Down`, `PgUp`, `PgDn`). Several combinations for one action: separate them with commas. No key: `none`. Changes apply at the next game start.

## Wheel, joystick and button-box buttons

Any hotkey can also be a button on a wheel rim, joystick or button box. In GrayHorizon Settings, click a hotkey box and press the button. It is added as the controller’s name and the button, for example `FANATEC Wheel:B12`. A hat direction is `HatUp`, `HatRight`, `HatDown` or `HatLeft`. Keys and buttons can share an action: `screenshot=F3, FANATEC Wheel:B12`.

- The game still sees a button you bind as a hotkey, so pick one the game does not use. The [menu](HUD-AND-SEAT.md#in-headset-menu-summary) is the exception: the game never gets the menu button, and it does not get the other menu buttons while the menu is open.
- One button for two hotkeys: the first in the list wins. Give each button one job.
- In the ini you can shorten the name to any part of it (`Fanatec:B12`). It is not case-sensitive.
- Seat buttons repeat while held.
- A controller plugged in after the game starts is found within 10 seconds.
- FH4 only reads a wheel’s first 32 buttons. A higher one can still be a hotkey.

Setting the menu up on a wheel’s D-pad is in [HUD-AND-SEAT.md](HUD-AND-SEAT.md#using-the-menu-on-a-wheel).

## Other ini options

| Key | Meaning |
|---|---|
| `vr` | `1` (default) = VR. `0` = the game plays on the monitor and the mod does nothing (no VR, no hotkeys, no status window). The **VR** box in GrayHorizon Settings. |
| `auto_start` | `1` (default) = VR starts by itself. `0` = only when you press F8. |
| `plain_views` | `auto` (default) = on for SteamVR. See [SteamVR](TECHNICAL.md#steamvr). `1` = always, `0` = never. |
| `srgb_swapchain` | `auto` or `1` = hand the picture over as the gamma-encoded form OpenXR expects. `0` = the game’s own format, as before 1.0.2. If the headset picture looks washed out or too dark, try the other value. |
| `stable_camera` | `1` removes the game’s simulated head motion. |
| `foveated` | `0` off, `1` quality, `2` balanced, `3` performance. |
| `hud_panels` | `0` (default) = HUD elements in the cockpit. `3` = the game’s flat HUD. |
| `hud_layer` | With an upscaler: `1` draws the HUD in its own layer at the full headset size, so dials and text stay sharp. |
| `tag_layer` | With an upscaler: `1` (default) draws name tags and checkpoint markers in their own layer, so the upscaler does not blur them. `0` = the older method. Can be changed while the game runs. |
| `other_cars` | With an upscaler: `1` (default) gives other cars their own motion, so they stay as sharp as the scenery while they move. `0` = off. Can be changed while the game runs. |
| `snow_fix` | FH4, canted mode: `1` (default) stops snow and rain being drawn as long sideways streaks. `2` = a simpler variant, `0` = off. Can be changed while the game runs. |
| `ui_scene` | FH4: `1` (default) = 3D only while the driving screen is up. Menus that keep the cockpit camera running behind them (car selection, blueprints, the map) are shown flat. `0` = the cockpit camera alone decides. FH5 and FH6 always work this way. |
| `start_early` | FH5 / FH6: `1` = VR from the boot screens. `0` = when the world has loaded. |
| `half_rate` | `1` = a new image every other headset frame. Less smooth. A last resort for a PC that cannot hold twice the headset rate. Eye timing warp stays off. |
| `console` | `1` opens GrayHorizon Settings when the game starts. |
| `safe_mode` | `1` turns every extra off for one run, without changing your other settings. |
| `mirror` | Minimum mirror resolution. The games’ menus cap it low. `0` = leave it alone. |
| `flicker_watch` | FH5 diagnostics. Leave at `0`. |
