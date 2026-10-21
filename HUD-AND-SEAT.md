# HUD layouts & seat position

## HUD elements

A normal flat HUD does not work in a headset — the corners are out of view.  
The mod takes the game’s HUD apart into separate elements (minimap, speedometer, radar, race info / lap times, pop-ups, etc.) and places each one as a floating panel in the cockpit.

- Turn an element off and it disappears from both the cockpit and the main view.
- The Speedometer row (or the panels hotkey) hides/shows the speedometer for the current session.
- `hud_panels=3` (or “HUD elements: Off” in GrayHorizon Settings) turns the whole system off and leaves the game’s flat HUD.

Leave the game’s HUD Safe Frame sliders at default.  
FH6: set Radar position to Center right, or the radar element stays empty.

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

Keyboard shortcuts still work while Adjust HUD is open (Tab, arrows, PgUp/PgDn, +/- , etc.).

## One layout per car

The first time you edit the HUD in a car, that car gets its own copy of the default layout.  
Changes are saved automatically when you exit the menu.  
“Save as the default for all cars” updates the default without touching cars that already have their own layout.

Capture areas are the same for every car (they describe the game’s HUD, not the car).

Per-car layouts require **Data Out** to be on (Settings → HUD and gameplay → Data Out: 127.0.0.1 port 20440). Without it, every change goes to the default.

Files (next to the ini, or in `Documents\GrayHorizon\FH*` on Game Pass):
- `gh4vr_panels.ini` / `gh5vr_panels.ini` / `gh6vr_panels.ini` — default layout and capture areas
- `gh4vr_car_hud.ini` / `gh5vr_car_hud.ini` / `gh6vr_car_hud.ini` — one section per car (`[ord_1234]`)

Delete a car’s section to put it back on the default.

## Seat position

The mod remembers a seat position per car.  
Adjust it from the in-headset menu (F12). It is saved with the car, the same way the HUD layout is.

## In-headset menu summary

F12 (or your bound button) opens a menu you drive with the D-pad or arrow keys.  
While it is open the game does not receive those buttons.

Options include:
- Recenter
- Seat position
- Speedometer on/off
- HUD layout (Adjust HUD)
- Screenshot (default F3)
- Flat view (menus/map/pause)
- Picture settings (trim, eye timing warp, etc.)

Each item shows its current value.
