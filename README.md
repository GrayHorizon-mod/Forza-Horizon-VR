# GrayHorizon: VR mods for Forza Horizon 4, 5 and 6

Not affiliated with Playground / Turn 10 / Xbox / Microsoft.  
Use at your own risk.

Three VR mods, one per game, that share the same design and the same settings program. Each gives you a stereo 3D cockpit view with full head tracking through OpenXR.

I made these after wanting a stable cam for a motion sim and the ability to see all HUD items such as the minimap, pinned items, lap/progress times, etc.  I could not find these in any other VR mod, and none existed for Forza Horizon 4 at all.

**Download:** <https://github.com/GrayHorizon-mod/Forza-Horizon-VR/releases/latest>: one zip per game, `GrayHorizon-FH4/5/6-<version>.zip`. Once installed, GrayHorizon Settings offers new versions by itself (see [Updates](#updates)).

GrayHorizon is free.  If it provides enjoyment for you, [tips are welcome](https://www.ko-fi.com/GrayHorizon), but you are under no obligation to do so.

| | |
|---|---|
| ![FH4 in LEGO Valley](https://raw.githubusercontent.com/GrayHorizon-mod/Forza-Horizon-VR/main/media/fh4-lego-valley.jpg)<br>*FH4, LEGO Valley: the minimap and speedometer placed on the dash* | ![FH5 Hot Wheels race](https://raw.githubusercontent.com/GrayHorizon-mod/Forza-Horizon-VR/main/media/fh5-hot-wheels.jpg)<br>*FH5, Hot Wheels: laps, position, checkpoint and skill score up front, the minimap on the dash* |
| ![FH6 in Tokyo](https://raw.githubusercontent.com/GrayHorizon-mod/Forza-Horizon-VR/main/media/fh6-tokyo.jpg)<br>*FH6, Tokyo: the minimap beside the wheel* | ![FH4 night race](https://raw.githubusercontent.com/GrayHorizon-mod/Forza-Horizon-VR/main/media/fh4-night-race.jpg)<br>*FH4, a night race: laps, times and position up front, the speedometer over the console* |
| ![FH5 at the top of a Hot Wheels loop](https://raw.githubusercontent.com/GrayHorizon-mod/Forza-Horizon-VR/main/media/fh5-loop.jpg)<br>*FH5: the top of a Hot Wheels loop, the stable camera keeps the cockpit steady* | ![FH5 open-wheeler under the Hot Wheels track](https://raw.githubusercontent.com/GrayHorizon-mod/Forza-Horizon-VR/main/media/fh5-open-wheeler.jpg)<br>*FH5: an open-wheeler under the Hot Wheels track, the minimap on its nose* |

*Screenshots taken with the mod's own screenshot key (F3): one eye's view, with the HUD elements where the headset shows them.*

| Game | Tested game version | Settings file | Log |
|---|---|---|---|
| Forza Horizon 4 | Steam 1.478.564.0 | `gh4vr.ini` | `gh4vr.log` |
| Forza Horizon 5 | Steam 1.688.109.0, Game Pass / Microsoft Store 3.688.109.0 | `gh5vr.ini` | `gh5vr.log` |
| Forza Horizon 6 | Steam 6.461.691.0, Game Pass / Microsoft Store 3.461.691.0 | `gh6vr.ini` | `gh6vr.log` |

A game update can move the things the mod hooks. On a version it does not recognise, the mod says so in its log and stays out of the way; the game then runs as normal, without VR.  Work is ongoing so the mod will work automatically when an update is released, except for FH4 of course.

## What you get

- **Stereo 3D cockpit view** with head tracking and body lean. The two eyes are drawn as alternating game frames, so the game has to run at **twice your headset's refresh rate** (144 fps for 72 Hz).
- **Eye timing warp.** Because the eyes are drawn on alternating frames, the left eye's picture is one frame older than the right one, and scenery passing the car at speed can look wrong in depth. The mod moves the left picture forward to the right eye's moment so both eyes match (see [Eye timing warp](#eye-timing-warp)).
- **Stable cockpit camera.** Removes the game's simulated head bob, g-force lean and crash jolts. Your head, and a motion rig if you have one, provide that.
- **Flat screen for menus, the map and pause**, in front of you in the headset.
- **The HUD in the cockpit.** The game's HUD is taken apart into elements (map, speedometer, race info, pop-ups ...) that float where you put them, with a layout for each car.
- **Per-car seat position**, remembered for each car.
- **Per-eye rendering, canted.** Each eye draws only what that eye sees, as a picture turned outward to match the lens. Fewer pixels for the same sharpness.
- **DLSS upscaling** (NVIDIA RTX), on by default. The game renders smaller and DLSS rebuilds the full size per eye. FH4 can also use AMD FSR.
- **The mod's own temporal anti-aliasing**, for when you don't use an upscaler. It removes the shimmer on trees, fences and fine detail that MSAA can't.
- **Detail as on the flat screen.** A headset's view is far wider than a monitor's, and the games take that as "zoomed out": other cars dropped to simple models and far scenery came in late. The mod corrects both (`detail_fov`, and the view it hands the game for culling).
- **Picture trim.** The canted picture is taller than the lenses show. `trim_top` / `trim_bottom` leave those rows undrawn: the same sharpness for fewer pixels.
- **Foveated rendering** (optional): coarser shading toward the edges of the view.
- **Settings per headset**: size, render scale, trim and foveated level for each headset or lens module.
- **Performance summary and verdict.** The mod measures frame rate and GPU load while you drive, says what is limiting, and suggests a size.
- **GrayHorizon Settings**, a small program for all of the above, with a live status view while the game runs.
- **Motion compensation** works through OpenXR-MotionCompensation if you have it.

## Requirements

- One of the game versions in the table above. FH5 and FH6 work from Steam and from Game Pass / the Microsoft Store (see [Game Pass and Microsoft Store](#game-pass-and-microsoft-store)); FH4 needs the Steam version.  There is no requirement to have the game installed in any particular folder.
- A PC VR headset with an **OpenXR** runtime. Tested: Pimax OpenXR and SteamVR (see the SteamVR section). A Meta Quest 3S over Meta Link worked in a short test of an earlier version, from before canted mode. Others (WMR, Virtual Desktop ...) should work but have not been tried.
- A strong CPU and GPU: the game must reach twice the headset's refresh rate.
- For DLSS: an NVIDIA RTX card. On any other card FH4 uses AMD FSR instead; FH5 and FH6 render the full size with the mod's own anti-aliasing.
- **Online play is at your own risk.** The mods hook the game's camera and rendering.  I personally have used these many hours online with no issues but do be aware.

## Install

Follow the steps for your copy of the game: **[Steam](#steam)** or **[Game Pass / Microsoft Store](#game-pass-and-microsoft-store)** (FH5 and FH6). Both end with the same [settings in the game](#game-settings).

### Steam

1. **Copy everything from the game's folder in the download into the game's own folder**, next to `ForzaHorizon4.exe` / `ForzaHorizon5.exe` / `ForzaHorizon6.exe` (in Steam: right-click the game, **Manage > Browse local files**):
   - `xinput1_3.dll` (the mod) and `openxr_loader.dll`
   - `GrayHorizon Settings.exe`
   - `gh4vr.ini` / `gh5vr.ini` / `gh6vr.ini` (the settings)
   - FH4 only: `nvngx_dlss.dll` for DLSS, and `amd_fidelityfx_loader_dx12.dll` and `amd_fidelityfx_upscaler_dx12.dll` for FSR. FH5 and FH6 have their own DLSS file.
2. **Set up the game:** see [Game settings](#game-settings) below.
3. **Start the game** with the headset connected and drive in **cockpit view**.
4. Press **Ctrl+Space** to recenter. (The mod also recenters by itself the moment the headset first reports that you are wearing it.)

The mod keeps its settings, log, HUD layout, seat positions and performance summary in the game folder (the `gh4vr*` / `gh5vr*` / `gh6vr*` files).

To uninstall, delete the files above and the `gh4vr*` / `gh5vr*` / `gh6vr*` files the mod creates in the game folder.

### Game Pass and Microsoft Store

FH5 and FH6 from Game Pass or the Microsoft Store. (FH4 is no longer sold or on Game Pass, and its old Store version cannot be modded: use the Steam version.)

1. **Find the game folder.** In the Xbox app, right-click the game, then **Manage > Files**. **Browse** opens the install folder; the game is in its **`Content`** folder, for example `C:\XboxGames\Forza Horizon 6\Content`, next to `ForzaHorizon5.exe` / `forzahorizon6.exe`. (Older installs show an **Enable advanced management features** button there: turn it on. If there is no such button, it is already on.)
2. **Copy everything from the game's folder in the download into that `Content` folder:** `xinput1_3.dll`, `openxr_loader.dll`, `GrayHorizon Settings.exe` and `gh5vr.ini` / `gh6vr.ini`. Windows asks for administrator permission: allow it.
3. **Rename `xinput1_3.dll` to `xinput1_4.dll`** in the `Content` folder. The Game Pass games load the mod under that name.
4. **Set up the game:** see [Game settings](#game-settings) below. The Game Pass version has its own video and HUD settings, separate from a Steam copy, so set them here too.
5. **Start the game** from the Xbox app with the headset connected and drive in **cockpit view**.
6. Press **Ctrl+Space** to recenter. (The mod also recenters by itself the moment the headset first reports that you are wearing it.)

**Where the settings go.** The game cannot write to its own folder, so the mod keeps its files in **`Documents\GrayHorizon\FH5`** or **`Documents\GrayHorizon\FH6`**: the ini (copied there from the `Content` folder on the first start), the log, the HUD layout, seat positions and the performance summary. Edit them there, or with GrayHorizon Settings, which opens with the game and uses that folder by itself. The ini in the `Content` folder is only the starting point.

**Updates** work as for Steam: GrayHorizon Settings replaces `xinput1_4.dll` and asks for administrator rights.

To uninstall, delete the files you copied into `Content` and the `Documents\GrayHorizon\FH5` / `FH6` folder.

If the game window on your monitor looks brighter or darker than the headset: Windows may apply Auto HDR to Store games on an HDR monitor. That only changes the monitor, not the headset; it can be switched off in the Windows display settings.

### Game settings

The same for every version of the games, in the game's own menus:

1. **Video settings: V-Sync off**, **frame rate unlocked**, **motion blur off**, **TAA/FXAA off**, **DLSS/FSR/Frame gen/XeSS/CAS, etc. off**.  Any other video enhancement besides MSAA (FH4/FH5) is unsupported, and it usually does not help at all.  You must use the mod's own TAA or DLSS/FSR.
2. **HDR off** (FH5 and FH6; FH4 has no HDR setting): **Settings > Video > HDR**, or turn HDR off in Windows (**Settings > Display > Use HDR**, or Win+Alt+B). The mod works with the game's normal 8-bit picture. With HDR on, the Meta / Quest runtime can't take the picture and VR stays off for that run. The status window and the log say so and tell you to turn HDR off.
3. **Settings > HUD and gameplay:** leave the **HUD Safe Frame** sliders at their default position. The HUD elements in the cockpit are made for it; with other values they come out cut off or empty.
4. **Settings > HUD and gameplay > Data Out: ON, IP address 127.0.0.1, port 20440.**  See [Data Out](#data-out-which-car-am-i-in) below if you're already using Data Out for SimHub, a motion rig or a dash.
5. FH6 only: **Settings > HUD and gameplay > Radar position: Center right.** The radar element in the cockpit is made for that position.

You never need to edit the game's own settings file: the mod writes the render size it needs before the game reads it.

### My settings

Here are my personal settings I have used after a lot of trial and error.  These are on a 9950X3D / 5090 and Pimax Crystal Super with both the Ultrawide and Micro-OLED modules.  While these will need to be tuned down for less powerful systems, hopefully this gives you a baseline to go by.  I would recommend lowering the DLSS render percentage if possible before the headset resolution, as its built-in scaler will not look as nice.

**Headset and mod settings.** For every game and both modules: resolution **Auto** (Pimax Play render quality 1.0, 72 Hz; that is 4504x5984 per eye on the Ultrawide), canted per-eye rendering, foveated rendering **Quality**.

| | FH4 | FH5 | FH6 |
|---|---|---|---|
| **Crystal Super Ultrawide** | DLSS 85% (set in the ini)<br>Trim 25% top / 30% bottom | DLSS 75% (set in the ini)<br>Trim 25% top / 30% bottom | DLSS 67% (quality)<br>Trim 25% top / 30% bottom |
| **Crystal Super Micro-OLED** | DLSS 85% (set in the ini)<br>Trim 25% top / 20% bottom | DLSS 67% (quality)<br>Trim 25% top / 20% bottom | DLSS 58% (balanced)<br>Trim 25% top / 20% bottom |

A percentage that is not one of the presets goes into the ini as `upscale_scale`, for example `upscale_scale=0.85` in the headset's section (see [Settings per headset](#settings-per-headset)).

**Game graphics settings.** Everything in step 1 of [Game settings](#game-settings) stays off in all three games.

**FH4:** every other setting at its maximum.

| FH5 | |
|---|---|
| Anisotropic Filter | High |
| Shadow Quality | Ultra |
| Night Shadows | On |
| Environment Texture | Ultra |
| Environment Geometry | Extreme |
| SSAO | High |
| Reflection | High |
| World Car LOD | Ultra |
| Deformable Terrain | Ultra |
| SSR | High |
| Lens Effects | Off |
| Shader | Ultra |
| Particle Effects | High |
| Ray Tracing | High |

| FH6 | |
|---|---|
| Car Level of Detail | Ultra |
| Environment Texture | Extreme |
| Environment Geometry | Extreme |
| Car Reflection | Medium |
| Screen Space Reflections | Medium |
| Raytraced Reflections | Off |
| Shadow | Ultra |
| Night Shadows | Off |
| Screen Space GI | Medium |
| Raytraced GI | Off |
| Shader | High |
| Deformable Terrain | Medium |
| Particle Effects | Medium |
| Volumetric Fog | Medium |
| Lens Effects | Off |

### The first start

The mod can only measure a headset's field of view while VR is running, so a headset it has never seen gets two steps:

- **First start:** the picture is sized from what the headset itself recommends, capped so a first start stays fast, with DLSS on and no trim. It works, but it is not yet as sharp or as fast as it will be.
- **Second start and after:** the mod knows the headset's field of view and uses the exact size for it. The log and the settings program say "restart to switch" after the first start.

The Pimax Crystal Super (Ultrawide and Micro-OLED modules) is recognised on the first start and comes with tuned size, render scale and trim.  However, since Pimax has silently shipped MANY different profiles for each headset, with every Pimax Play release seemingly getting a different one, these may not match what your headset reports even if it is one of these.

## GrayHorizon Settings

`GrayHorizon Settings.exe` sits in the game folder and edits that game's ini for you. The mod opens it when the game starts (turn that off with "Open this window when the game starts", or `console=0`); you can also start it by hand at any time.

![GrayHorizon Settings while FH5 runs: settings and hotkeys on the left, live performance and status on the right](https://raw.githubusercontent.com/GrayHorizon-mod/Forza-Horizon-VR/main/media/settings.png)

- **Left side:** the headset these settings are for, resolution, per-eye mode, anti-aliasing / upscaling, DLSS render scale, foveated rendering, trim, HUD elements on / off, the Data Out port and where its packets are passed on to, and the other on/off options.
- **VR** and **Start VR by itself:** untick **VR** and the game plays as normal on the monitor, for example when someone else plays: no VR, no hotkeys, no status window. At the next start the game's resolution goes back to the monitor's. Untick **Start VR by itself** and VR only comes on when you press the VR key (F8).
- **Right side:** every hotkey, editable.
- **While the game runs** it shows the live status: frame rate, GPU load, what each feature is doing.
- **Performance summary** opens the statistics file from your last drive. **Use the suggested size** fills in the size the mod worked out.

Changes are saved to the ini and apply the next time the game starts.

## Performance: reading the verdict

The in-headset VR performance display lets you see what the performance looks like for the last 30 seconds (default hotkey F6) and gives advice.  For a smaller "numbers only" display, use the frame rate readout (default hotkey F5).

The mod also writes `gh4vr_stats.txt` / `gh5vr_stats.txt` / `gh6vr_stats.txt` every 30 seconds of VR driving.

- **Pairs per second** is what matters: it should equal your headset's refresh rate.
- **GPU load in the mid 80s is already the limit.** The eyes are drawn as alternating frames, so the GPU runs out of time well before it reads 100%.
- **Below full rate with the GPU at 80% or more:** the GPU is the limit. Lower the resolution or a graphics setting.
- **Below full rate with the GPU under 80%:** it is mostly the CPU or the game itself. A lower resolution will help little; lower the settings that load the CPU (geometry and environment detail), or try `detail_fov=80`.
- Dense city areas are the hardest in all three games, for both CPU and GPU.  Be warned, Tokyo in FH6 is brutal on both CPU and GPU.

### Increasing performance
- Turn MSAA off and use DLSS if possible.
- Picture Trim: Saving here can be HUGE.  Trim the top/bottom to where you can still see the entire image in the headset.  This could reduce your CPU and GPU load by a significant amount.
- Enable foveated rendering
- Turn off the eye timing warp (`afr_warp=0`, the checkbox in GrayHorizon Settings, or Ctrl+Shift+F10 in game). It costs a little GPU time per frame; if you never notice the depth problem it fixes, you won't miss it.
- Try lowering all graphics settings to a low preset, then slowly turn them up until the CPU or GPU is at its limit.  I recommend keeping the environment detail as high as possible to keep things from "popping in" as they get closer to you.
- The performance summary does a good job of providing estimates for resolution size.  You can try using those, or if using DLSS, change the setting to a lower percentage.

## Updates

When GrayHorizon Settings opens, it checks GrayHorizon's GitHub page for a newer version for this game. If there is one, an **Update to x.y.z** button appears at the bottom; it shows what's new and installs the update when you agree.

- The game has to be closed. The button stays until you use it.
- Only the mod's files are replaced. Your settings (`gh?vr.ini`) and HUD layout (`gh?vr_panels.ini`) are never part of an update.
- Every update is signed by GrayHorizon, and each file is checked against that signature before anything in the game folder changes. A download that does not match is thrown away and nothing changes.
- If GrayHorizon Settings itself was updated, it restarts by itself.
- If Windows does not allow changes in the game folder, it asks for administrator rights.
- `gh?vr_update.log` in the game folder (Game Pass: in `Documents\GrayHorizon\FH5` / `FH6`) records every check and install.
- Turn the check off with "Look for GrayHorizon updates on GitHub when this window opens" (`update_check=0`). The mod never contacts the internet itself.

The version you have is shown in GrayHorizon Settings' status line, and in the Details tab of `xinput1_3.dll`'s Properties in Explorer.

## Resolution

`resolution=` in the ini (or the first box in GrayHorizon Settings):

| Value | Meaning |
|---|---|
| `auto` | The size from the table for the headset that is connected (see below). |
| `WIDTHxHEIGHT` | A fixed size per eye, for every headset. |
| `off` | Leave the game's own setting alone. |

With `auto`, the mod recognises the headset by its field of view (for example `L67_R45_U57_D57`: outer, inner, up, down in degrees) and looks its size up in the ini:

```ini
[resolutions_canted]
L67_R45_U57_D57=4504x5984
```

`[resolutions_canted]` is used in canted mode, `[resolutions]` otherwise. One line per headset, so a headset with swappable lens modules keeps a size for each; a module the mod has already seen in VR is recognised at launch.

The size is that of the **untrimmed** picture. The mod rounds it to multiples of 8.

**How large?** Drive for a few minutes, then look at the performance summary. It gives a verdict and, when the GPU is the limit, a suggested size.

## Eye timing warp

The two eyes are drawn on alternating game frames, so the left eye's picture is one frame older than the right one it is shown with. In that frame the car moves on (about 40 cm at 200 km/h), and everything passing the car is in a slightly different place in each eye. Your eyes read that as depth: roadside objects can look nearer and smaller than they are, and the road beside the car can seem to rise toward the windows. Some people notice it straight away, others never do.

The eye timing warp fixes it. Before each pair goes to the headset, every pixel of the left picture is moved to where it is one frame later, using the scene's depth: the scenery by the car's movement, other cars by their own, and your own car's cockpit by the car body's. Both eyes then show the same moment.

- On by default (`afr_warp=1`). Switch it with **Ctrl+Shift+F10** in game, or the "Eye timing warp" checkbox in GrayHorizon Settings.
- Needs an upscaler (DLSS, or FSR in FH4): it uses the depth the upscaler is given. Without one it does nothing.
- Not used with SteamVR's plain views or with `half_rate=1`.
- It costs a little GPU time per frame. If you are short of frame rate and don't notice the depth problem, turn it off.
- Where something close (a window pillar, another car) uncovers scenery that was hidden a frame earlier, that spot is filled from the background next to it. At very high speed you may see a slight smear along such edges.

## Per-eye rendering

| Mode | ini | What it is |
|---|---|---|
| Canted (recommended) | `per_eye=1`, `canted=1` (FH4, FH6) or `canted=2` (FH5) | Each eye's picture is turned outward to the middle of that eye's view. All of the game's effects work. |
| Off-center (experimental) | `per_eye=1`, `canted=0` | Each eye's exact skewed view. Some of the games' effects can't handle a skewed view (see Known issues). |
| Off | `per_eye=0` | One wide picture for both eyes. Simplest, and the most pixels for the same sharpness. |

### Picture trim (canted mode)

```ini
trim_top=10
trim_bottom=10
```

Percent of the picture's height, 0 to 40 each, that is not drawn. Start at 0 and raise each until you can just see the black edge when you look up or down, then go back a step. A headset the mod has not seen starts at 0 / 0. The Crystal Super modules come with 25 / 30 (Ultrawide) and 25 / 20 (Micro-OLED).

## Anti-aliasing and upscaling

| Choice | ini | Notes |
|---|---|---|
| DLSS | `upscale=dlss` | The fastest sharp picture. `upscale_scale` is how much of the size the game renders first: `0.67` quality, `0.58` balanced, `0.5` performance, `1.0` = anti-aliasing only. |
| FSR (FH4 only) | `upscale=fsr` | Any DirectX 12 GPU. Not as clean as DLSS: thin lines shimmer a little. Chosen by itself when `upscale=dlss` meets a card that is not an RTX. |
| The mod's temporal AA | `upscale=off`, `anti_aliasing=1` | Native size. `taa_sharpness` 0 to 1. |
| None | `upscale=off`, `anti_aliasing=0` | |

- `upscale_sharpness` (0 to 1) sharpens after DLSS.
- `dlss_preset=auto` picks the model for your card; a letter forces one.
- With an upscaler, turn the game's MSAA off for the most speed.
- The cost of DLSS goes with the size it **outputs**, not the size the game renders. If the GPU is the limit, lowering the resolution helps more than lowering `upscale_scale`.

## Detail distances: `detail_fov`

```ini
detail_fov=auto
```

The field of view the game works its detail distances out for.

| Value | Meaning |
|---|---|
| `auto` | The game's own field of view for the view: detail as on the flat screen. |
| a number (degrees) | Between the game's own and the headset's: less detail, less work. |
| `0` | Off: the headset's own field of view. Other cars turn into simple models much closer. |

In FH6 this is the difference between other cars looking right and looking dark and dithered. In FH4 it makes little visible difference.


## HUD elements

A flat HUD does not work in a headset: its corners are out of sight. The mod takes the game's HUD apart into **elements** (minimap, speedometer, radar, the whole top strip with race position and lap times, pop-ups and so on) and hangs each one in the cockpit as a small floating panel. You decide where each one sits, how big it is and whether you want it at all.

- An element you switch off is gone: it is not drawn in the cockpit and not on the main view either.
- The `panels` hotkey hides and shows the speedometer, for cars whose own dials are enough. It lasts until you close the game.
- `hud_panels=3` (or "HUD elements: Off" in GrayHorizon Settings) turns the whole system off and leaves the game's flat HUD.

**Leave the game's HUD Safe Frame sliders at their default position** (Settings > HUD and gameplay). The built-in capture areas are made for it, and the mod then fits them to any resolution, trim and headset by itself.

**FH6: set Radar position to Center right** (same menu). In another position the radar element stays empty until you move its capture area there (see below).

FH4 has an element of its own, `center`, for the large banners in the middle of the screen ("10 MINUTES REMAINING", "CHECKPOINT MISSED"). Where two of FH4's rectangular capture areas overlap, the smaller one keeps the shared part and the larger one leaves it out, so nothing is shown twice.

### Arranging the HUD

Press the `calibration` hotkey. A box in the headset names the element you are adjusting and lists the keys; it follows your head, so look away from an element to see it clearly. While calibrating, these keys do not reach the game:

| Key | Does |
|---|---|
| Tab | Next element |
| Ctrl+Tab | This element on / off |
| Arrows (Shift: fine) | Move it in the cockpit, 1 cm (1 mm) |
| PgUp / PgDn | Farther / nearer |
| + / - | Larger / smaller |
| Ctrl + plus / minus | Opacity of the element itself (100% = solid) |
| Ctrl+PgUp / PgDn | Dark background behind it (0% = none, 100% = solid) |
| Alt + arrows (Shift: x10) | Move the capture area, the piece of the game's HUD the element shows |
| Ctrl + arrows | Resize the capture area |
| F1 | Show the key list again |

Hold a key to repeat it. Press the `calibration` hotkey again to save.

Opacity and background are for the elements that are always on screen: map, speedometer, drive mode box (FH5/FH6), and radar (FH6). The others come and go and are drawn solid.

### One layout per car

Cars differ: a dash that hides the map in one car is empty space in the next. So a layout belongs to the car you made it in.

- The first time you calibrate in a car, that car gets its own copy of **every** element's place, size, opacity, background and on / off. It keeps them from then on, whatever you change elsewhere.
- Cars you have not calibrated use the **default** layout.
- The `hud_save_default` hotkey (Ctrl+Shift+F3) makes whatever is on screen right now the default. Cars with their own layout are not touched.
- The capture areas are the same for every car: they describe the game's HUD, not the car.

The message on leaving calibration says where it was saved: "for this car" or "as the default".

Per-car layouts need the game's **Data Out** (next section), which tells the mod which car you are in. Without it every change goes to the default.

Files, next to the ini: `gh4vr_panels.ini` / `gh5vr_panels.ini` / `gh6vr_panels.ini` hold the default layout and the capture areas (written the first time you calibrate or save; until then the built-in layout is used); `gh4vr_car_hud.ini` / `gh5vr_car_hud.ini` / `gh6vr_car_hud.ini` hold one section per car (`[ord_1234]`). Delete a car's section to put it back on the default.

## Data Out: which car am I in

The games can send telemetry ("Data Out") as UDP packets. The mod reads the car's number from them, so seat positions and HUD layouts are kept per car model.

In the game: **Settings > HUD and gameplay > Data Out: ON, IP address 127.0.0.1, port 20440.**

```ini
telemetry=1
telemetry_port=20440
telemetry_forward=
```

- **Already using Data Out** for SimHub, a motion rig or a dash app? Point the game at the mod's port as above and put the program's old address into `telemetry_forward`, for example `telemetry_forward=127.0.0.1:8888`. The mod passes every packet on unchanged.
- **Several programs:** separate up to eight targets with commas, for example `telemetry_forward=127.0.0.1:8888, 127.0.0.1:9999`. Each is `ip:port` with the ip in numbers.
- Both settings are in GrayHorizon Settings as **Data Out port** and **Pass Data Out on to**.
- Without Data Out the mod tells cars apart by where the game puts the driver's eyes. That works for the seat position most of the time, but it is not reliable enough for HUD layouts.
- `telemetry=0` turns it off.

## Per-car seat position

The seat hotkeys move your eye point 1 cm at a time; hold them to repeat. The position is saved for the car you are in (`[seats]` in the ini); other cars use the default. Delete a car's line to put it back.

## Settings per headset

If you use more than one headset, or one headset with different lens modules, each can have its own render scale, trim and foveated level, besides its own size. GrayHorizon Settings has a **Headset** list at the top: pick one, give it a name, and the size, scale, foveated level and trim below it are that headset's. The mod recognises the headset when the game starts and uses its set.

In the ini it is a section per headset, named after its field of view. A value that is missing there is taken from `[settings]`.

```ini
[headset_L67_R45_U57_D57]
name=Pimax Crystal Super Ultrawide
upscale_scale=0.67
trim_top=25
trim_bottom=30
foveated=1
```

## Hotkeys

They work while the game window has focus, and every one can be changed in GrayHorizon Settings or under `[hotkeys]` in the ini.

| Default | Name | Action |
|---|---|---|
| F8 | `vr_toggle` | VR on / off |
| Ctrl+Space | `recenter` | Recenter |
| F2 | `flat_view` | Flat view on / off: the whole game screen in front of you |
| Ctrl+Up / Ctrl+Down | `seat_forward` / `seat_back` | Seat forward / back 1 cm |
| Ctrl+PgUp / Ctrl+PgDn | `seat_up` / `seat_down` | Seat up / down 1 cm |
| F7 | `calibration` | HUD calibration on / off (off saves) |
| F11 | `panels` | Speedometer element off / on (until the game is closed) |
| Ctrl+Shift+F3 | `hud_save_default` | The HUD layout on screen becomes the default |
| F5 | `fps` | Frame rate readout in the headset |
| F6 | `performance` | Performance display in the headset |
| F9 | `console` | Status window show / hide |
| F10 | `foveated` | Foveated rendering: next level |
| F12 | `stable_camera` | Stable camera on / off |
| Ctrl+Shift+F10 | `afr_warp` | Eye timing warp on / off (see [Eye timing warp](#eye-timing-warp)) |
| Ctrl+Shift+F12 | `anti_aliasing` | Temporal anti-aliasing on / off |
| Ctrl+Shift+PgUp / PgDn | `taa_sharper` / `taa_softer` | Sharpening +/- 0.1 |
| Ctrl+Shift+F11 | `per_eye` | Per-eye rendering on / off (FH4 only) |
| F3 | `screenshot` | Screenshot of what you see in the headset, HUD elements included (a JPEG in `Pictures\GrayHorizon`; the flat screen in menus) |
| F4 | `frame_capture` | Capture for a problem report (large files in the game folder) |

The everyday keys are plain function keys so they can be reached with a headset on. The Horizon games do not use the function keys themselves.

Write a key on its own or with `Ctrl`, `Shift` and/or `Alt` (`F1`-`F24`, `A`-`Z`, `0`-`9`, `Space`, `Up`, `Down`, `PgUp`, `PgDn` ...). Several combinations for one action: separate them with commas. No key: `none`. Changes apply at the next game start.

## SteamVR

The mods work with SteamVR as the OpenXR runtime. Two things are different there, and the mods handle both by themselves:

- **Picture format.** SteamVR only accepts the sRGB form of the game's picture format. The mod uses it when the plain one is not offered. The pixels are the same.
- **Plain views.** Each eye's picture is drawn turned outward (canted mode) and, with `trim_top` / `trim_bottom`, without its top and bottom rows. SteamVR does not show such a picture correctly: it comes out stretched, most on the inner side of each eye, and the two eyes do not line up. On SteamVR the mod therefore redraws each finished picture into SteamVR's own view before handing it over. Rendering, upscaling and the HUD are unchanged, so canted mode and the trim keep their saving. With a trim, the rows not drawn are black.

The log says which is in use: `xr: plain views ON` or `off`. `plain_views` in the ini is `auto` by default (on for SteamVR, off elsewhere); `1` forces it on, `0` off. If a picture looks stretched or will not fuse on another runtime, try `plain_views=1`.

**What it costs.** Measured on a Pimax Crystal Super (Micro-OLED) with an RTX 5090, same route and settings in each game:

| Game | Runtime | Stereo pairs/s | GPU load |
|---|---|---|---|
| FH5 | Pimax OpenXR | 70.9 | 87% |
| FH5 | SteamVR, plain views | 70.4 | 91% |
| FH4 | Pimax OpenXR | 71.8 | 87% |
| FH4 | SteamVR, plain views | 72.1 | 93% |

About the same frame rate, with 4 to 6 points less GPU in hand on SteamVR. The redrawn picture is very slightly softer than the original.

**Which runtime to use.** If your headset has its own OpenXR runtime (Pimax OpenXR for Pimax headsets), use that. Use SteamVR when it is the only runtime your headset has.

**Picture size.** SteamVR's render resolution slider sets the size it recommends, and `resolution=auto` follows it. Set SteamVR to 100% before you compare sizes or frame rates. If SteamVR drops to half the headset's rate (its motion smoothing), the game is not keeping up: lower the resolution or `upscale_scale`.

Tested with SteamVR 2.18 and Pimax's SteamVR driver. Other headsets on SteamVR have not been tried yet, and a Meta Quest 3S (over Meta Link, Meta's own runtime) has only been tried with a version from before canted mode. Plain views do not switch on by themselves there. If the picture looks stretched or the eyes do not line up on your headset, set `plain_views=1` and please report it.

## Other settings

| Key | Meaning |
|---|---|
| `vr` | `1` (default) = VR. `0` = the game plays as normal on the monitor and the mod does nothing (no VR, no hotkeys, no status window), e.g. when someone else plays. At the next start the game's resolution goes back to the monitor's if it is still the headset size; Data Out is still passed on. The **VR** box in GrayHorizon Settings. |
| `auto_start` | `1` (default) = VR starts by itself. `0` = only when you press the VR key (F8). |
| `plain_views` | `auto` (default) = on for SteamVR: each eye's picture is redrawn into the runtime's own view before it is handed over (see SteamVR). `1` = always, `0` = never. |
| `srgb_swapchain` | `auto` (default) or `1` = the picture is handed to the headset marked as gamma-encoded (the sRGB form of the game's format), as the OpenXR standard expects. `0` = in the game's own format, as before 1.0.2. If the picture looks too bright and washed out, or too dark, in your headset, try the other value. |
| `mirror` | Minimum mirror resolution (the games' menus cap it low; `0` = leave alone). |
| `stable_camera` | `1` removes the game's simulated head motion. |
| `foveated` | `0` off, `1` quality, `2` balanced, `3` performance. |
| `hud_panels` | `0` (default) = the HUD as elements in the cockpit, `3` = off: the game's flat HUD. |
| `hud_layer` | With an upscaler: `1` draws the HUD into its own layer at the full headset size (sharp dials and text). |
| `tag_layer` | With an upscaler: `1` (default) draws name tags and checkpoint markers into their own layer, so they stay out of the upscaler and come out sharp. `0` = the older method. Can be changed while the game runs. |
| `other_cars` | With an upscaler: `1` (default) gives other cars their own motion, so they stay as sharp as the scenery while they move. `0` = off. Can be changed while the game runs. |
| `snow_fix` | FH4, canted per-eye mode: `1` (default) keeps snow and rain from being drawn as long sideways streaks (the game stretches each flake by the camera's movement since the last frame, which with alternating eyes was the other eye's direction). `2` = a simpler variant, `0` = off. Can be changed while the game runs. |
| `ui_scene` | FH4: `1` (default) = 3D only while the game's driving screen is up; menus that keep the cockpit camera running behind them (car selection, blueprint menus, the map) are shown flat. `0` = the cockpit camera alone decides. FH5 and FH6 always work this way. |
| `start_early` | FH5 / FH6: `1` = VR from the boot screens on, `0` = when the world has loaded. |
| `afr_warp` | `1` (default): the eye timing warp, both eyes shown at the same moment (see [Eye timing warp](#eye-timing-warp)). `0` = off. |
| `half_rate` | For slower PCs: `1` = a new image every other headset frame. Less smooth; a last resort. |
| `console` | `1` opens GrayHorizon Settings with the live status when the game starts. |
| `safe_mode` | `1` turns every extra off for one run, without changing your other settings. |
| `flicker_watch` | FH5 diagnostics: `1` records eye images that come out doubled or too bright. Leave at `0`. |

## Reporting a problem

Open an issue at <https://github.com/GrayHorizon-mod/Forza-Horizon-VR/issues>, with:

1. **Try safe mode** (`safe_mode=1`, or the box in GrayHorizon Settings). If the problem is gone, turn the extras back on one at a time to find which causes it.
2. **Attach the log** from the game folder (Game Pass: `Documents\GrayHorizon\FH5` / `FH6`), from a run where the problem happened. It is replaced at each launch; FH5 and FH6 keep the previous three as `...prev1.log` to `...prev3.log`. Its summary block (`==== summary`) lists your GPU, headset, OpenXR runtime and layers, and every setting. If the game crashed, the end of the log has a short crash report saying where.
3. **Say what you saw and when:** in the cockpit or a menu, one eye or both, after which hotkey.

## Known issues

- **Off-center per-eye mode** (`canted=0`): some of the games' own effects can't handle a skewed view. In FH4, grass and rock particles flash in the right eye and SSAO shades wrongly near the bottom of the windshield. Canted mode has none of this.
- **Shadows and textures still come in at the game's own distance.** That is the same on the flat screen.
- **Some older car models are missing parts of the body** you would never see from the driver's seat on a monitor (rear doors, for example). You can see that by turning your head.
- **Other cars with an upscaler.** The upscaler needs to know how everything moves. The mod works that out for the scenery, your own car and the nearest 16 other cars within 250 m. What is left:
  - a car that has just appeared can take up to 2 seconds to be picked up, and looks pixelated until then (most visible with oncoming traffic at very high closing speeds);
  - wheels are treated as part of the body, so spinning wheels stay a little rough;
  - every vehicle is treated as car-sized, so trucks and buses are only partly covered;
  - beyond the nearest 16, and with the mod's own temporal AA instead of an upscaler, other cars are not tracked.
- **After a game update** the mod may stay inactive until it is updated.
- **OpenXR Toolkit** is kept out of FH4 because its layer crashes the game (`openxr_toolkit=1` lets it load, at your own risk).

## Source code

The source is not public yet. It will be published later under the same license.

## How it works

`xinput1_3.dll` is a proxy: it forwards every XInput call to the real Windows DLL. On load it hooks the game's camera objects by giving them private copies of their virtual tables. The game's code and read-only data are never modified. It also hooks DXGI Present and runs an OpenXR session on the game's own D3D12 device, handing each eye's finished image to the headset.

## Credits

Built by GrayHorizon with Claude (Anthropic). OpenXR loader and headers (c) The Khronos Group Inc. Sharpening based on AMD FidelityFX RCAS (MIT). Upscaling uses NVIDIA DLSS and AMD FidelityFX Super Resolution. NVIDIA, RTX and DLSS are trademarks of NVIDIA Corporation. AMD, FidelityFX and FSR are trademarks of Advanced Micro Devices, Inc.

## License

**PolyForm Noncommercial 1.0.0** (see `LICENSE.md`). You may use, share and modify these mods for any noncommercial purpose. Selling them, or using them commercially, is not permitted. Third-party files keep their own licenses (see `THIRD_PARTY_NOTICES.md`).
