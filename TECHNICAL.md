# Technical details

This page covers the deeper options. Most people never need to touch these.

## Eye timing warp

The two eyes are drawn on alternating game frames, so the left eye’s picture is one frame older than the right. At speed this can make roadside objects look nearer or smaller than they are.  
The warp moves the left picture forward to the right eye’s moment using the scene depth so both eyes match.  
On by default (`afr_warp=1`). Needs an upscaler. Costs a little GPU. Turn it off if you don’t notice the problem and want the frames.

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

