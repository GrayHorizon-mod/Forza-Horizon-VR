## GrayHorizon Settings app

`GrayHorizon Settings.exe` is included in every zip.  
It shows live status while the game is running, lets you change most options without editing the ini by hand, and checks for updates on GitHub. In FH3 it also has a **Start Forza Horizon 3** button. The mod opens it when the game starts. Turn that off with “Open this window when the game starts”, or `console=0`.

The live panel at the top shows the frame rate, GPU and CPU load while the game runs, with a graph. The yellow line under the graph is the advice from the performance summary, for example *Limited by the CPU: reduce graphics quality settings*.

The settings are on four tabs. Changes apply the next time the game starts.

- **Picture**: the headset profile, [learning mode](#learning-mode), **Size per eye** (35% to 150% of the headset's full size, with marks at the common sizes), per-eye rendering, anti-aliasing (DLSS, FSR, TAA or none), render scale, foveated rendering, trim, and **Frame timing**: *Eye timing warp* and *Run at half frame rate*.
- **Options**:
  - **Enable GrayHorizon** unticked: the game plays on the monitor as normal (no VR, no hotkeys, no status window).  At the next start the resolution goes back to your in-game setting before using this mod.
  - **VR enabled on startup** unticked (`auto_start=0`): VR comes on only when you press F8.
  - Also: stable camera, opening this window when the game starts, safe mode, and looking for updates.
  - **Reset to defaults**: puts the ticked parts back to how a new install has them: settings and hotkeys, seat positions, HUD layouts, and (not ticked unless you tick it) the learned picture size, which makes learning mode start over. Close the game first. Your current files are copied into a `GrayHorizon backup <date> <time>` folder next to them, so nothing is lost.
- **Menu**: the keys and buttons for the [in-headset menu](HUD-AND-SEAT.md#in-headset-menu-summary).
- **Hotkeys**: the hotkeys. Several keys and buttons are allowed: separate them with commas. Click a box and type a key's name (with modifiers, such as `Ctrl + Shift + A`), or press a wheel or controller button to have it filled in.

Most used hotkeys:
- F12 (or a wheel/pad button) — in-headset menu
- F5 — frame-rate readout
- F6 — performance summary (last 30 seconds)
- Ctrl+Space — recenter

The full list is under [Hotkeys](#hotkeys). Wheel and button-box buttons are there too.

## Learning mode

**Experimental.** GrayHorizon learns the picture size (and the render scale, with DLSS or FSR) that suits your PC over a few short drives. It aims to keep the GPU just below its limit, so the headset gets a new frame every time.

1. **The first start with a new headset**: the mod sets itself up for it. The headset says *Restart the game now: learning mode starts then.*
2. **Learning drives**: each drive is one game start. Drive at least 3 minutes (the headset shows *Learning mode: drive 1 of 3*), then restart the game when it says so. Each drive tries a different size. Drive where the game is busiest, such as a downtown area with many buildings and cars. Sometimes a 4th or 5th drive is needed to confirm the result.
3. **Done**: the headset says *Learning mode done ... Restart the game to use it.* The size and render scale it found are your settings from then on. Fine-tune them on the Picture tab if you like.

Good to know:
- Learning mode does **not** change anti-aliasing. Pick it first: DLSS on NVIDIA RTX cards, FSR on other cards. TAA works too on a powerful PC.
- It does not change the game's own graphics settings. If the result is not smooth or sharp enough, lower some of the game's graphics quality settings and run learning mode again.
- Without DLSS or FSR it only learns the size.
- It starts by itself for a new install, a new headset, a swapped lens module, or another per-eye mode. Start it again any time: Picture tab → **Start learning mode**.
- **Stop learning mode** (same button, while it runs) keeps the size it is on now, under your control on the slider.

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
| Ctrl+Shift+F11 | `per_eye` | Per-eye rendering on / off (FH3 and FH4) |
| F3 | `screenshot` | What you see in the headset, HUD included. A JPEG in `Pictures\GrayHorizon` (FH3: the `Screenshots` folder in its `LocalState`). The flat screen while in a menu. |
| F4 | `frame_capture` | Capture for a problem report. Large files in the game folder (FH3: `LocalState`). |

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

Setting the menu up on a wheel’s D-pad is in [HUD-AND-SEAT.md](HUD-AND-SEAT.md#using-the-menu-on-a-wheel-or-a-controller).

## Other config file options

| Key | Meaning |
|---|---|
| `detail_fov` | `auto`, a number, or `0`. Controls how far the game draws detailed models. |
| `mip_bias` | `auto`, `off`, or a number. With DLSS or FSR: sharper textures, matched to the render scale. If a texture shimmers or goes missing, try `off`. |
| `plain_views` | `auto` (default) = on for SteamVR and Meta Link (any runtime whose log line says `fovMutable 0`). See [SteamVR](TECHNICAL.md#steamvr). `1` = always, `0` = never. |
| `srgb_swapchain` | `auto` or `1` = hand the picture over as the gamma-encoded form OpenXR expects. `0` = the game’s own format, as before 1.0.2. If the headset picture looks washed out or too dark, try the other value. |
| `hud_panels` | `0` (default) = HUD elements in the cockpit. `3` = the game’s flat HUD. |
| `hud_layer` | With an upscaler: `1` draws the HUD in its own layer at the full headset size, so dials and text stay sharp. |
| `tag_layer` | With an upscaler: `1` (default) draws name tags and checkpoint markers in their own layer, so the upscaler does not blur them. `0` = the older method. Can be changed while the game runs. |
| `other_cars` | With an upscaler: `1` (default) gives other cars their own motion, so they stay as sharp as the scenery while they move. `0` = off. Can be changed while the game runs. |
| `snow_fix` | FH3 / FH4, canted mode: `1` (default) stops snow and rain being drawn as long sideways streaks. `2` = a simpler variant, `0` = off. Can be changed while the game runs. |
| `ui_scene` | FH4: `1` (default) = 3D only while the driving screen is up. Menus that keep the cockpit camera running behind them (car selection, blueprints, the map) are shown flat. `0` = the cockpit camera alone decides. FH5 and FH6 always work this way. |
| `no_wheel_view` | `flat` (default) = the cockpit view without the steering wheel goes to the flat screen, like the hood and bumper views. `3d` = keep it in VR. |
| `start_early` | FH5 / FH6: `1` (default) = VR from the boot screens. `0` = when the world has loaded. |
| `eye_tag_guard` | `1` (default) = the game's own render queue tells the mod which frame it is drawing, and left and right images are kept in order from that. It corrects a slip within a few frames, after menus and rewinds too. `0` = only the older check of the frame queue's depth. Leave it on. |
| `flat_zoom` | The flat screen's size in the headset (menus, the map, the hood and bumper views): `-5` to `5`, about 10% a step. `0` (default) = 3 m wide. Also in the in-headset menu: Video → Flat screen size. |
| `flicker_watch` | FH5 diagnostics. Leave at `0`. |
