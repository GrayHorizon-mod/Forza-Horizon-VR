# Performance

The mod draws the two eyes as alternating game frames, so the game must run at **twice** your headset’s refresh rate (example: 144 fps for a 72 Hz headset).  
“Pairs per second” in the performance tools is what matters — it should match the headset refresh.

## Reading the numbers

GrayHorizon Settings and the in-headset menu show a performance summary.  
- GPU load in the mid-80s is already the practical limit. The eyes are alternating, so the GPU runs out of time well before 100%.  
- Below full rate with GPU ≥ \~80%: GPU limited. Lower resolution, trim more, drop a graphics setting, or lower DLSS percentage.  
- Below full rate with GPU under \~80%: mostly CPU or the game itself. Lowering resolution helps less. Drop geometry/environment detail or try `detail_fov=80`.  
- Dense cities are the hardest areas in all three games (Tokyo in FH6 is especially rough).

The mod also writes `gh4vr_stats.txt` / `gh5vr_stats.txt` / `gh6vr_stats.txt` every 30 seconds of VR driving.

## Quick ways to gain performance

1. Turn the game’s MSAA off and use DLSS if you have an NVIDIA RTX card.  
2. Picture trim (canted mode): raise `trim_top` / `trim_bottom` until you can just see the black edge when looking up/down, then back off a step. This can save a lot of pixels.  
3. Enable foveated rendering.  
4. Turn off eye timing warp (`afr_warp=0`) if you don’t notice the depth issue it fixes. It costs a little GPU time.  
5. Drop to a low graphics preset, then raise settings until you hit the limit. Keep environment detail as high as you can to reduce pop-in.  
6. Use the performance summary’s suggested resolution when it offers one.

## Example baseline (high-end)

These are the author’s personal numbers on a 9950X3D + RTX 5090 with a Pimax Crystal Super (both Ultrawide and Micro-OLED modules), 72 Hz, canted per-eye, foveated Quality.  
Tune down for less powerful systems. Prefer lowering the DLSS render percentage before dropping headset resolution.

| Module              | FH4              | FH5              | FH6              |
|---------------------|------------------|------------------|------------------|
| Crystal Super Ultrawide | DLSS 85%, trim 25/30 | DLSS 75%, trim 25/30 | DLSS 67% (quality), trim 25/30 |
| Crystal Super Micro-OLED | DLSS 85%, trim 25/20 | DLSS 67% (quality), trim 25/20 | DLSS 58% (balanced), trim 25/20 |

Graphics were kept high (environment geometry Extreme, etc.) with ray-traced effects mostly off. These are a starting point, not a requirement.

## Resolution setting

In the `.ini` or GrayHorizon Settings:

- `auto` — size from the per-headset table (recommended)  
- `WIDTHxHEIGHT` — fixed size per eye  
- `off` — leave the game’s own setting alone  

With `auto` the mod matches the headset by its field-of-view string and looks up the size in `[resolutions_canted]` (or `[resolutions]`).

See [SETTINGS.md](SETTINGS.md) for the full ini reference and [TECHNICAL.md](TECHNICAL.md) for eye timing warp, canted rendering, trim, and detail_fov.
