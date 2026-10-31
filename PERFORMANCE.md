# Performance

The mod draws the two eyes as alternating game frames, so the game must run at **twice** your headset’s refresh rate (example: 144 fps for a 72 Hz headset).  
“Pairs per second” in the performance tools is what matters — it should match the headset refresh.

## Reading the numbers

GrayHorizon Settings and the in-headset menu show a performance summary.  
- GPU load in the mid-90s is already the practical limit. The eyes are alternating, so the GPU runs out of time well before 100%.  
- Below full rate with GPU ≥ \~90%: GPU limited. Lower resolution, trim more, drop a graphics setting, or lower DLSS percentage.  
- Below full rate with GPU under \~90%: mostly CPU or the game itself. Lowering resolution helps less. Drop geometry/environment detail.  
- Dense cities are the hardest areas in every game (Tokyo in FH6 is especially rough).

The mod also writes `gh3vr_stats.txt` / `gh4vr_stats.txt` / `gh5vr_stats.txt` / `gh6vr_stats.txt` every 30 seconds of VR driving.

**Environment detail:** Keep Environment Geometry / Environment Texture as high as you can (Extreme if possible). Lowering them makes cones, barriers, and other roadside objects pop in late, which is very noticeable in the headset. Drop other settings first.

## Quick ways to gain performance

1. Turn the game’s MSAA off and use DLSS if you have an NVIDIA RTX card.  
2. Picture trim (canted mode): Raise Trim top/bottom percentage until you can just see the black edge when looking up/down, then back off a step. This can save a lot of pixels.  
3. Enable foveated rendering.
4. Turn off eye timing warp if you don’t notice the depth issue it fixes. It costs a little GPU time.  
5. Drop to a low graphics preset, then raise settings until you hit the limit. Keep environment detail as high as you can to reduce pop-in.  
6. Run [learning mode](SETTINGS.md#learning-mode) to find the size that suits your PC.
7. Enabling half-rate draws a new image every other headset frame.  It is not as smooth, and a last resort when the PC cannot hold twice the headset rate. Eye timing warp stays off while it is on.

## Example baseline (high-end)

These are the author’s personal numbers on a 9950X3D + RTX 5090 with a Pimax Crystal Super (both Ultrawide and Micro-OLED modules), 72 Hz, canted per-eye, foveated Quality.  
Tune down for less powerful systems. Prefer lowering the DLSS render percentage before dropping headset resolution. DLSS spends its time on the size it outputs, so once you are GPU-limited a smaller resolution helps more than a lower percentage. Try the lower percentage first anyway: it usually looks better. 85% and 75% are not presets. Set them with the **Render scale** slider on the Picture tab of GrayHorizon Settings.

| Module              | FH4              | FH5              | FH6              |
|---------------------|------------------|------------------|------------------|
| Crystal Super Ultrawide | DLSS 85%, trim 25/30 | DLSS 75%, trim 25/30 | DLSS 67% (quality), trim 25/30 |
| Crystal Super Micro-OLED | DLSS 85%, trim 25/20 | DLSS 67% (quality), trim 25/20 | DLSS 58% (balanced), trim 25/20 |

Game settings that went with those numbers. Everything in the [required video settings](README.md#quick-start) stays off in all three games. FH4: every other setting at its maximum.

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

Graphics were kept high, with the ray-traced effects mostly off, as in the tables. These are a starting point, not a requirement.

See [SETTINGS.md](SETTINGS.md) for the config file options, including detail_fov, and [TECHNICAL.md](TECHNICAL.md) for eye timing warp, canted rendering and trim.
