# Install

Not affiliated with Playground Games, Turn 10, Xbox, or Microsoft.  
Use at your own risk. Official downloads are only from the [Releases](https://github.com/GrayHorizon-mod/Forza-Horizon-VR/releases/latest) page.

One zip per game: `GrayHorizon-FH4-<version>.zip`, `GrayHorizon-FH5-<version>.zip`, or `GrayHorizon-FH6-<version>.zip`.

## Steam

1. Download the zip for your game.
2. Right-click the game in Steam → Manage → Browse local files.
3. Copy everything from the zip into that folder (next to `ForzaHorizon4.exe` / `ForzaHorizon5.exe` / `ForzaHorizon6.exe`):
   - `xinput1_3.dll` (the mod) and `openxr_loader.dll`
   - `GrayHorizon Settings.exe`
   - `gh4vr.ini` / `gh5vr.ini` / `gh6vr.ini`
   - FH4 only: the DLSS and FSR DLLs included in the zip
4. Set the game settings (see [SETTINGS.md](SETTINGS.md)).
5. Start the game with the headset connected and switch to cockpit view.
6. Press `Ctrl+Space` to recenter. The mod also recenters automatically the first time the headset reports you are wearing it.

Settings, log, HUD layout, seat positions, and performance files stay in the game folder (`gh4vr*`, `gh5vr*`, or `gh6vr*`).

Uninstall: delete the files you copied plus the `gh?vr*` files the mod created.

## Game Pass / Microsoft Store (FH5 and FH6 only)

FH4 is no longer sold or on Game Pass. Its old Store version cannot be modded — use the Steam version.  
If you have FH4 progress on the old Store/Game Pass version, the separate [FH4 Save Converter](https://github.com/GrayHorizon-mod/FH4-Save-Converter) can move a profile to Steam (or back) if you own both and are signed in with the same Xbox account.

1. In the Xbox app, right-click the game → Manage → Files. Browse to the install folder. The game is in the `Content` folder (example: `C:\XboxGames\Forza Horizon 6\Content`).
   - Older installs may show an “Enable advanced management features” button — turn it on if present.
2. Copy everything from the zip into that Content folder:
   - `xinput1_3.dll`, `openxr_loader.dll`, `GrayHorizon Settings.exe`, and the `.ini`
3. Windows will ask for administrator permission — allow it.
4. Rename `xinput1_3.dll` to `xinput1_4.dll` in the Content folder. Game Pass versions load the mod under that name.
5. Set the game settings (see [SETTINGS.md](SETTINGS.md)). Game Pass has its own video/HUD settings, separate from any Steam copy.
6. Launch from the Xbox app with the headset connected and switch to cockpit view.
7. Press `Ctrl+Space` to recenter.

**Where settings are stored:** the game cannot write to its own folder, so the mod keeps its files in `Documents\GrayHorizon\FH5` or `Documents\GrayHorizon\FH6`. The `.ini` in the Content folder is only the starting copy. Edit the one in Documents (or use GrayHorizon Settings, which uses that folder automatically).

Updates: GrayHorizon Settings replaces `xinput1_4.dll` and will ask for administrator rights if needed.

Uninstall: delete the files you copied into Content and the `Documents\GrayHorizon\FH5` or `FH6` folder.

**Note:** If the game window on your monitor looks brighter or darker than the headset, Windows may be applying Auto HDR to Store games. That only affects the monitor. Turn it off in Windows display settings if you want them to match.

## Updates

GrayHorizon Settings checks the GitHub Releases page when it opens. If a newer version exists, an update button appears.  
- The game must be closed.  
- Only the mod’s files are replaced. Your `.ini` and HUD layout are left alone.  
- Every update is signature-checked.  
- You can turn the check off in Settings.

## Uninstall summary

- Steam: delete the DLLs, Settings exe, and the `gh?vr*` files in the game folder.  
- Game Pass: delete the files in the Content folder and the `Documents\GrayHorizon\FH*` folder.
