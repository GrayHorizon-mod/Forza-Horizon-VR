# Install

Official downloads are only from the [Releases](https://github.com/GrayHorizon-mod/Forza-Horizon-VR/releases/latest) page.

One zip per game: `GrayHorizon-FH3-<version>.zip`, `GrayHorizon-FH4-<version>.zip`, `GrayHorizon-FH5-<version>.zip`, or `GrayHorizon-FH6-<version>.zip`.

Forza Horizon 3 installs differently from the others: see [Forza Horizon 3](#forza-horizon-3).

## Steam

1. Download the zip for your game.
2. Right-click the game in Steam → Manage → Browse local files.
3. Copy everything from the zip into that folder (next to `ForzaHorizon4.exe` / `ForzaHorizon5.exe` / `ForzaHorizon6.exe`):
   - `xinput1_3.dll` (the mod) and `openxr_loader.dll`
   - `GrayHorizon Settings.exe`
   - `gh4vr.ini` / `gh5vr.ini` / `gh6vr.ini`
   - FH4: the DLSS and FSR DLLs included in the zip. FH5: the FSR DLLs included in the zip
4. Set the game settings (see [Quick start](README.md#quick-start)).
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
5. Set the game settings (see [Quick start](README.md#quick-start)). Game Pass has its own video/HUD settings, separate from any Steam copy.
6. Launch from the Xbox app with the headset connected and switch to cockpit view.
7. Press `Ctrl+Space` to recenter.

**Where settings are stored:** the game cannot write to its own folder, so the mod keeps its files in `Documents\GrayHorizon\FH5` or `Documents\GrayHorizon\FH6`. The `.ini` in the Content folder is only the starting copy. Edit the one in Documents (or use GrayHorizon Settings, which uses that folder automatically).

Updates: GrayHorizon Settings replaces `xinput1_4.dll` and will ask for administrator rights if needed.

Uninstall: delete the files you copied into Content and the `Documents\GrayHorizon\FH5` or `FH6` folder.

**Note:** If the game window on your monitor looks brighter or darker than the headset, Windows may be applying Auto HDR to Store games. That only affects the monitor. Turn it off in Windows display settings if you want them to match.

## Forza Horizon 3

FH3 runs in Windows’ app sandbox. That changes two things:

- **SteamVR must be the default OpenXR runtime** (SteamVR settings → OpenXR). Other runtimes, Pimax’s for example, cannot run from inside the sandbox. A Pimax headset works through SteamVR.  If SteamVR is not the runtime, the game simply starts without VR.
- **The mod is started by its own launcher**, not by putting files into the game folder.

**Microsoft Store install (the usual one, in `C:\Program Files\WindowsApps`):**

1. Unzip `GrayHorizon-FH3-<version>.zip` into a folder of your own (Documents, `D:\Games`, ...), not into Program Files. Keep its files together.
2. Start FH3 with `GrayHorizon FH3.exe`, or open `GrayHorizon Settings.exe` and press **Start Forza Horizon 3** (bottom right).

- The launcher gives FH3 permission to read that one folder (no administrator rights needed) and starts the game with the mod. FH3 started from the Start menu or the Xbox app stays the plain game. Some antivirus programs distrust launchers that load a mod into a game this way. If yours blocks `GrayHorizon FH3.exe`, allow it for this folder.

**A copy of FH3 in a normal folder you can write to:** 

- If your install has a developer mode, turn that option on.

- Close FH3, rename the game’s `GFSDK_Aftermath_Lib_UWP.x64.dll` to `gfsdk_orig.dll`, copy all the files from the zip into the game folder, and start FH3 as usual. If `gfsdk_orig.dll` is already there, the mod is installed: skip the rename, or it replaces the game’s own DLL with the mod.

**Where its files are:** the sandbox only lets FH3 write to its own data folder, `%LOCALAPPDATA%\Packages\Microsoft.OpusPG_8wekyb3d8bbwe\LocalState` (paste that into Explorer’s address bar). The settings, log, HUD layout and seat positions are there (`gh3vr*`), and F3 screenshots go into its `Screenshots` folder. GrayHorizon Settings finds them by itself.

**DLSS:** NVIDIA keeps its DLSS files in `C:\ProgramData\NVIDIA\NGX`, which the sandbox cannot read.  On the Microsoft Store install, DLSS does not start yet, even with permission: NVIDIA’s driver turns it down (`0xbad00002` in the log). Use FSR or TAA there.

On a copy in a normal folder, DLSS works once FH3 has that permission. Open Command Prompt as administrator and run this once (the uninstaller shows the command to take it back):

```
icacls "C:\ProgramData\NVIDIA\NGX" /grant "*S-1-15-2-1987231219-3494637732-3076478737-3503969843-3465841799-2831659819-1889736820:(OI)(CI)(RX)"
```

**Intel Arc:** the launcher does not load FH3ArcFix yet.

**Uninstall:** close FH3 and GrayHorizon Settings, run `Uninstall GrayHorizon FH3.cmd` from the mod’s folder (it says what it will do and asks first), then delete the folder. The mod never changes the game’s files or your saves. On a copy in a normal folder, also rename `gfsdk_orig.dll` back.

## Updates

GrayHorizon Settings checks the GitHub Releases page when it opens. If a newer version exists, an update button appears.  
- The game must be closed.  
- Only the mod’s files are replaced. Your `.ini` and HUD layout are left alone.  
- Every update is signature-checked. A download that does not match is thrown away and nothing changes.  
- If GrayHorizon Settings itself was updated, it restarts.  
- `gh?vr_update.log` records every check and install (Game Pass: in `Documents\GrayHorizon\FH5` or `FH6`).  
- Only GrayHorizon Settings contacts the internet, and only for this check. The mod itself does not.  
- The version is shown in GrayHorizon Settings, and on the Details tab of the mod DLL in Explorer.  
- You can turn the check off in Settings.

## Uninstall summary

- Steam: delete the DLLs, Settings exe, and the `gh?vr*` files in the game folder.  
- Game Pass: delete the files in the Content folder and the `Documents\GrayHorizon\FH*` folder.
- FH3: run `Uninstall GrayHorizon FH3.cmd`, then delete the mod’s folder.
