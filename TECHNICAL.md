# Technical details

This page covers the deeper options. Most people never need to touch these.

## Eye timing warp

The two eyes are drawn on alternating game frames, so the left eye’s picture is one frame older than the right. At speed this can make roadside objects look nearer or smaller than they are.  
The warp moves the left picture forward to the right eye’s moment using the scene depth so both eyes match.  
On by default (`afr_warp=1`). Needs an upscaler. Costs a little GPU. Turn it off if you don’t notice the problem and want the frames.

- At 200 km/h the car moves about 40 cm in that one frame. The road beside the car can seem to rise toward the windows. Some people notice it straight away. Others never do.
- Switch it in the headset menu (**Video → Eye timing warp**) or with the checkbox in GrayHorizon Settings.
- It uses the depth an upscaler is given (DLSS, or FSR in FH4). Without an upscaler it does nothing.
- It is not used with SteamVR’s plain views, or with `half_rate=1`.
- Where something close (a window pillar, another car) uncovers scenery that was hidden a frame earlier, that spot is filled from the background next to it. At very high speed you may see a slight smear along those edges.

## Per-eye rendering

| Mode | ini | Notes |
|------|-----|-------|
| Canted (recommended) | `per_eye=1`, `canted=1` (FH4/FH6) or `canted=2` (FH5) | Each eye’s picture is turned outward. All game effects work. |
| Off-center (experimental) | `per_eye=1`, `canted=0` | Exact skewed view. Some effects break. |
| Off | `per_eye=0` | One wide picture for both eyes. Most pixels. |

## Picture trim (canted mode)

`trim_top` / `trim_bottom` = percent of height (0–40) that is not drawn.  
Start at 0 and raise until you can just see the black edge when looking up or down, then back off one step.  
The Crystal Super modules ship with 25/30 (Ultrawide) and 25/20 (Micro-OLED).

## detail_fov

Controls the field of view the game uses for detail distances.  
- `auto` — same detail as on a flat screen (recommended)  
- a number — between the game’s FOV and the headset’s  
- `0` — headset FOV (other cars drop to simple models sooner)

In FH6 this is the difference between other cars looking correct vs dark and dithered.

## SteamVR

The mods work with SteamVR as the OpenXR runtime. Two things are different there, and the mods handle both by themselves:

- **Picture format.** SteamVR only accepts the sRGB form of the game’s picture format. The mod uses it when the plain one is not offered. The pixels are the same.
- **Plain views.** Each eye’s picture is drawn turned outward (canted mode) and, with `trim_top` / `trim_bottom`, without its top and bottom rows. SteamVR does not show that picture correctly: it comes out stretched, most on the inner side of each eye, and the two eyes do not line up. On SteamVR the mod redraws each finished picture into SteamVR’s own view before handing it over. Rendering, upscaling and the HUD are unchanged, so canted mode and the trim keep their saving. With a trim, the rows not drawn are black.

The log says which is in use: `xr: plain views ON` or `off`. `plain_views` in the ini is `auto` by default (on for SteamVR, off elsewhere). `1` forces it on, `0` forces it off. If a picture looks stretched or will not fuse on another runtime, try `plain_views=1`.

**What it costs.** Measured on a Pimax Crystal Super (Micro-OLED) with an RTX 5090, same route and settings in each game:

| Game | Runtime | Stereo pairs/s | GPU load |
|---|---|---|---|
| FH5 | Pimax OpenXR | 70.9 | 87% |
| FH5 | SteamVR, plain views | 70.4 | 91% |
| FH4 | Pimax OpenXR | 71.8 | 87% |
| FH4 | SteamVR, plain views | 72.1 | 93% |

About the same frame rate, with about 4 to 6 points more GPU load on SteamVR. The redrawn picture is very slightly softer than the original.

**Which runtime to use.** If your headset has its own OpenXR runtime (Pimax OpenXR for a Pimax headset), use that. Use SteamVR when it is the only runtime your headset has.

**Picture size.** SteamVR’s render-resolution slider sets the size it recommends, and `resolution=auto` follows it. Set SteamVR to 100% before you compare sizes or frame rates. If SteamVR drops to half the headset’s rate (its motion smoothing), the game is not keeping up: lower the resolution or `upscale_scale`.

Tested with SteamVR 2.18 and Pimax’s SteamVR driver. Other headsets on SteamVR have not been tried yet. A Meta Quest 3S over Meta Link, on Meta’s own runtime, has only been tried with a version from before canted mode. Plain views do not switch on by themselves there. If the picture looks stretched or the eyes do not line up, set `plain_views=1` and please report it.

## Known issues

- **Off-center per-eye mode** (`canted=0`): some of the game’s own effects cannot handle a skewed view. In FH4, grass and rock particles flash in the right eye, and SSAO shades wrongly near the bottom of the windshield. Canted mode does not do this.
- **Shadows and textures still come in at the game’s own distance.** That is the same on a monitor.
- **Some older car models are missing bodywork** you would never see from the driver’s seat on a monitor (a rear door, for example). Turning your head shows it.
- **Other cars with an upscaler.** The mod works out motion for the scenery, your own car, and the nearest 16 other cars within 250 m. A car that has just appeared can take up to 2 seconds to be picked up, and looks pixelated until then (most visible with oncoming traffic at very high closing speeds). Wheels are treated as part of the body, so spinning wheels stay a little rough. Every vehicle is treated as car-sized, so trucks and buses are only partly covered. Beyond the nearest 16, and when you use the mod’s own temporal AA instead of an upscaler, other cars are not tracked.
- **After a game update** the mod may stay inactive until it is updated for that version. The game still runs, without VR.
- **OpenXR Toolkit** is kept out of FH4 because its layer crashes the game. `openxr_toolkit=1` lets it load, at your own risk.

## How it works

`xinput1_3.dll` (Game Pass: `xinput1_4.dll`) is a proxy. It forwards every XInput call to the real Windows DLL. On load it hooks the game’s camera objects by giving them private copies of their virtual tables. The game’s code and read-only data are never modified. It also hooks DXGI Present and runs an OpenXR session on the game’s own D3D12 device, handing each eye’s finished image to the headset.
