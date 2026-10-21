# HUD layouts & seat position

## HUD elements

A normal flat HUD does not work in a headset — the corners are out of view.  
The mod takes the game’s HUD apart into separate elements (minimap, speedometer, radar, race info / lap times, pop-ups, etc.) and places each one as a floating panel in the cockpit.

- Turn an element off and it disappears from both the cockpit and the main view.
- The Speedometer row (or the panels hotkey) hides/shows the speedometer for the current session.
- `hud_panels=3` (or “HUD elements: Off” in GrayHorizon Settings) turns the whole system off and leaves the game’s flat HUD.

Leave the game’s HUD Safe Frame sliders at the stock position for that game. Forza Horizon 4 is Horizontal 8, Vertical 37. Forza Horizon 5 and 6 use their own stock positions; do not copy the Horizon 4 numbers.  
FH6: set Radar position to Center right, or the radar element stays empty.

FH4 has a `center` element for the large banners in the middle of the screen (“10 MINUTES REMAINING”, “CHECKPOINT MISSED”). Where two of FH4’s capture areas overlap, the smaller one keeps the shared part, so nothing is drawn twice.

## Arranging the HUD (in-headset menu)

Press F12 (or the button you set) to open the menu, then choose **Adjust HUD**.

| Row | Action |
|-----|--------|
| Element | Left/right to pick which one |
| On/off | Toggle this element |
| Move it | Enter, then arrows move it (1 cm steps). Enter or Back when done |
| Distance | Nearer / farther |
| Size | Smaller / larger |
| Opacity | 0–100% (always-on elements only) |
| Background | Dark backing behind it (0–100%) |
| Capture area | Move/resize the piece of the game’s HUD it shows |
| Save as default for all cars | Makes the current layout the default |

Back saves the layout for the current car and returns to the main menu.  
Hold a direction to repeat.

Opacity and background only apply to always-on elements (map, speedometer, drive mode box, FH6 radar). The others appear and disappear and are drawn solid.

While Adjust HUD is open, the old calibration keys work too: Tab (next element), Ctrl+Tab (on / off), arrows (move; Shift = 1 mm), PgUp / PgDn (farther / nearer), + / - (size), Ctrl + plus / minus (opacity), Ctrl+PgUp / PgDn (background), Alt + arrows (move the capture area; Shift = 10 pixels), Ctrl + arrows (resize it).

## One layout per car

All HUDs can be moved so they look right. In a large truck you may want the race info higher than in a small car.

The first time you edit the HUD in a car, that car gets its own copy of the default layout.  
Changes are saved automatically when you exit the menu.  
“Save as the default for all cars” updates the default without touching cars that already have their own layout.

The message on leaving Adjust HUD says where it was saved: for this car, or as the default. The panels file is written the first time you edit or save. Until then the built-in layout is used.

Capture areas are the same for every car (they describe the game’s HUD, not the car).

Per-car layouts require **Data Out** to be on (Settings → HUD and gameplay → Data Out: 127.0.0.1 port 20440). Without it, every change goes to the default.

Files (next to the ini, or in `Documents\GrayHorizon\FH*` on Game Pass):
- `gh4vr_panels.ini` / `gh5vr_panels.ini` / `gh6vr_panels.ini` — default layout and capture areas
- `gh4vr_car_hud.ini` / `gh5vr_car_hud.ini` / `gh6vr_car_hud.ini` — one section per car (`[ord_1234]`)

Delete a car’s section to put it back on the default.

## Data Out

The games can send telemetry (“Data Out”) as UDP. The mod reads the car’s number from it, which is how seat positions and HUD layouts are kept per car.

In the game: **Settings → HUD and gameplay → Data Out: ON, IP address 127.0.0.1, port 20440.**

```ini
telemetry=1
telemetry_port=20440
telemetry_forward=
```

- **Already using Data Out** for SimHub, a motion rig or a dash? Point the game at the mod’s port, as above, and put the program’s old address in `telemetry_forward`, for example `telemetry_forward=127.0.0.1:8888`. The mod passes every packet on unchanged.
- **Several programs:** up to eight, separated by commas, for example `telemetry_forward=127.0.0.1:8888, 127.0.0.1:9999`. Each one is `ip:port` with the ip in numbers.
- Both are in GrayHorizon Settings as **Data Out port** and **Pass Data Out on to**.
- Without Data Out, the mod tells cars apart by where the game puts the driver’s eyes. That works for the seat position most of the time. It is not reliable enough for HUD layouts, so every HUD change goes to the default.
- `telemetry=0` turns it off.

## Seat position

The seat rows in the headset menu, or the seat hotkeys (Ctrl+Up / Ctrl+Down, Ctrl+PgUp / Ctrl+PgDn), move your eye point 1 cm at a time. Hold to repeat. The position is saved for the car you are in, under `[seats]` in the ini. Other cars use the default. Delete a car’s line to put it back.

## In-headset menu summary

Press **F12** (or the button you give it). The menu opens in the lower part of the view, so the windshield stays in sight. Every row shows what it is set to now.

- **Recenter** (selected when the menu opens: Enter recenters and closes it)
- **Seat forward / back** and **Seat up / down** (left / right, 1 cm a step, shown in cm)
- **Speedometer** on / off
- **Adjust HUD**
- **Screenshot** (F3). A JPEG of what you see, HUD included, in `Pictures\GrayHorizon`. In a menu it saves the flat screen.
- **Video**: frame rate, performance display, stable camera, anti-aliasing, sharpness, foveated rendering, eye timing warp
- **Flat view** on / off: the whole game screen in front of you

Up / down choose a row, left / right change it, Enter selects, Back goes back a page or closes the menu. Notifications such as the frame rate still show, just above the menu.

F4 (`frame_capture`) is not in the menu. It writes large files in the game folder for a problem report.

| Default | Name | Action |
|---|---|---|
| F12 | `menu` | Open / close |
| Up / Down, D-pad | `menu_up` / `menu_down` | Choose a row |
| Left / Right, D-pad | `menu_left` / `menu_right` | Change the row |
| Enter, A | `menu_enter` | Select |
| Esc, B | `menu_back` | Back / close |

`XInput` in a binding (`XInput:HatUp`, `XInput:B1`) means any Xbox-style pad, whatever Windows calls it.

**What the game sees.** Only the menu button is always kept from the game. The other controls reach the game as usual, except while the menu is on screen. Then the game does not get them (keys, pad and wheel buttons alike), and a button pressed in the menu stays hidden until you let go. FH4 only reads a wheel’s first 32 buttons. A higher one can still be a hotkey.

## Using the menu on a wheel

The menu is made for a wheel’s D-pad: open it, change the seat or the HUD, and close it without taking your hands off the rim.

1. Open GrayHorizon Settings. The **Menu in the headset** box at the top of the hotkeys is laid out like a D-pad: Up at the top, Left and Right at the sides, Enter in the middle, Down below.
2. Click **Open / close** and press the rim button you want. The game never gets this button, so pick one you do not need in the game.
3. Click **Up** and press up on the wheel’s D-pad. Do the same for **Down**, **Left** and **Right**. The box then reads like `Up, FANATEC Wheel:HatUp`.
4. Click **Enter** and **Back** and press a rim button for each. The buttons the game uses to confirm and go back are a natural fit: the game does not get them while the menu is open.
5. Click **Save**. The game picks the change up the next time it starts.

Pressing a button adds it to what is already in the box, so the keyboard key stays and both work. To take a button out, delete it from the box along with its comma. While the menu is closed, the D-pad and the Enter and Back buttons work in the game as usual.

Any other hotkey can be a wheel or button-box button too. See [Wheel, joystick and button-box buttons](SETTINGS.md#wheel-joystick-and-button-box-buttons).
