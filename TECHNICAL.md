# Technical details

This page covers the deeper options. Most people never need to touch these.

## Eye timing warp

The two eyes are drawn on alternating game frames, so the left eye’s picture is one frame older than the right. At speed this can make roadside objects look nearer or smaller than they are.  
The warp moves the left picture forward to the right eye’s moment using the scene depth so both eyes match.  
On by default. Needs an upscaler. Costs a little GPU. Turn it off if you don’t notice the problem and want higher performance.

- At 200 km/h the car moves about 40 cm in that one frame. The road beside the car can seem to rise toward the windows. Some people notice it straight away. Others never do.
- Switch it in the headset menu (**Video → Eye timing warp**) or with the checkbox in GrayHorizon Settings.
- It uses the depth an upscaler is given (DLSS or FSR). Without an upscaler it does nothing.
- It is not used with plain views (SteamVR and Meta Link, see below), or when running at half frame rate.
- Where something close (a window pillar, another car) uncovers scenery that was hidden a frame earlier, that spot is filled from the background next to it. At very high speed you may see a slight smear along those edges.

## Per-eye rendering

| Mode | Notes |
|------|-------|
| Canted (recommended) | Each eye’s picture is turned outward. All game effects work. |
| Off-center (experimental) | Exact skewed view. Some effects break. |
| Off | One wide picture for both eyes. Most pixels. |

## Picture trim (canted mode)

Start at 0 and raise until you can just see the black edge when looking up or down, then back off one step.  
The Crystal Super modules ship with 25/30 (Ultrawide) and 25/20 (Micro-OLED).

## SteamVR

The mods work with SteamVR as the OpenXR runtime. Two things are different there, and the mods handle both by themselves:

- **Picture format.** SteamVR only accepts the sRGB form of the game’s picture format. The mod uses it when the plain one is not offered. The pixels are the same.
- **Plain views.** Each eye’s picture is drawn turned outward (canted mode) and SteamVR does not show that picture correctly: it comes out stretched, most on the inner side of each eye, and the two eyes do not line up. On SteamVR the mod redraws each finished picture into SteamVR’s own view before handing it over. Rendering, upscaling and the HUD are unchanged, so canted mode and the trim keep their saving. With a trim, the rows not drawn are black.

Performance is about the same frame rate, with about 4 to 6 percent more GPU load on SteamVR. The redrawn picture is very slightly softer than the original.

The log says which is in use: `xr: plain views ON` or `off`. 

**Which runtime to use.** If your headset has its own OpenXR runtime (Pimax OpenXR for a Pimax headset), use that. Use SteamVR when it is the only runtime your headset has.  **FH3 requires SteamVR**

**Picture size.**  Set SteamVR to 100% before you compare sizes or frame rates. If SteamVR drops to half the headset’s rate (its motion smoothing), the game is not keeping up: lower the resolution or DLSS/FSR scaling.

**Meta Link.** A Meta Quest 3 over Meta Link, on Meta’s own runtime, needs plain views too. That runtime does not let the game choose its own field of view, so it shows the canted pictures as if they were its own views. Each eye looks right on its own, but with both eyes open you see strong double vision.  The mod will automatically switch to plain views in this case.  Virtual Desktop lets the game choose, so it does not need them.

## Forza Horizon 3

FH3 is a Microsoft Store app and runs in Windows’ app sandbox (an AppContainer). Three things follow from that:

- **The launcher.** A Store app cannot simply load a DLL from its folder, and its folder cannot be written to. `GrayHorizon FH3.exe` starts the game through Windows’ package debug setting, loads the mod and lets the game run (the technique uwpinject shows; credited in THIRD_PARTY_NOTICES). It gives FH3 read permission on the mod’s folder only, and clears the debug setting again after each start.
- **SteamVR only.** The sandbox cannot reach most OpenXR runtimes’ services. SteamVR’s works.
- **Files in LocalState.** Settings, logs and HUD layouts live in FH3’s own data folder (see [Forza Horizon 3](INSTALL.md#forza-horizon-3)).

## Known issues

- **Off-center per-eye mode**: some of the game’s own effects cannot handle a skewed view. In FH4, grass and rock particles flash in the right eye, and SSAO shades wrongly near the bottom of the windshield. Canted mode does not do this.
- **Shadows and textures still come in at the game’s own distance.** That is the same on a monitor.
- **Some older car models are missing bodywork** you would never see from the driver’s seat on a monitor (a rear door, for example). Turning your head shows it.
- **Other cars with an upscaler.** The mod works out motion for the scenery, your own car, and the nearest 16 other cars within 250 m. A car that has just appeared can take up to 2 seconds to be picked up, and looks pixelated until then (most visible with oncoming traffic at very high closing speeds). Wheels are treated as part of the body, so spinning wheels stay a little rough. Every vehicle is treated as car-sized, so trucks and buses are only partly covered. 
- **After a game update** the mod may stay inactive until it is updated for that version. The game still runs, without VR.
- **FH3, Microsoft Store install: DLSS does not start.** NVIDIA’s driver turns it down from inside the sandbox (`0xbad00002` in the log). FSR works.
- **FH3 on Intel Arc:** the launcher does not load FH3ArcFix yet.
- **OpenXR Toolkit** is kept out of FH4 because its layer crashes the game. `openxr_toolkit=1` lets it load, at your own risk.

## How it works

`xinput1_3.dll` (Game Pass: `xinput1_4.dll`) is a proxy. It forwards every XInput call to the real Windows DLL. FH3’s mod is `GFSDK_Aftermath_Lib_UWP.x64.dll`, which its launcher loads into the game. On load the mod hooks the game’s camera objects by giving them private copies of their virtual tables. The game’s code and read-only data are never modified. It also hooks DXGI Present and runs an OpenXR session on the game’s own D3D12 device, handing each eye’s finished image to the headset.
