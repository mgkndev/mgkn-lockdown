# mgkn — Lockdown Protocol UE4SS Script

A lightweight UE4SS-based script for Lockdown Protocol. Gives you server-validated item giving, heal, and ammo features — works whether you're hosting or joining.

> **Note:** Use this in lobbies you host or play in with friends, or when testing solo. Using it in a public lobby with people who haven't agreed to it isn't fair to them, and can get you kicked or banned.

---

## Requirements

* Lockdown Protocol (Steam)
* `ue4ss.zip` from this repo (signed UE4SS build for Lockdown Protocol)
* `mgkn.zip` from this repo

---

## Installation

### 1 ) Install UE4SS

1. Download `ue4ss.zip` from this repo and extract it.
2. Copy its contents (the `ue4ss` folder/files and `dwmapi.dll`) into:

```
   Steam\\steamapps\\common\\LOCKDOWN Protocol\\LockdownProtocol\\Binaries\\Win64
   ```

3. Launch the game once, let it reach the main menu, then close it. This lets UE4SS generate its initial files (logs, `Mods` folder, `mods.txt`, etc.).

### 2 ) Add the mgkn script

1. Download `mgkn.zip` and extract the `mgkn` folder inside it.
2. Copy the `mgkn` folder into:

```
   ...\\Binaries\\Win64\\ue4ss\\Mods
   ```

   The final path should look like:

```
   ...\\Binaries\\Win64\\ue4ss\\Mods\\mgkn\\Scripts\\main.lua
   ```

3. Open `...\\Binaries\\Win64\\ue4ss\\Mods\\mods.txt` in a text editor and add this line:

```
   mgkn : 1
   ```

   It should sit alongside the other entries, like this:

```
   CheatManagerEnablerMod : 1
   ConsoleCommandsMod : 1
   ConsoleEnablerMod : 1
   SplitScreenMod : 0
   LineTraceMod : 1
   BPML_GenericFunctions : 1
   BPModLoaderMod : 1
   mgkn : 1

   ; Built-in keybinds, do not move up!
   Keybinds : 1
   ```

### 3 ) Launch the game

1. Start Lockdown Protocol.
2. In-game, press **F10** or **`~`** (tilde) to open the UE4SS console.

   * If F10 is mapped to a media key (volume/brightness) on your laptop, try `Fn + F10`.
   * If neither opens it, try `~`.
3. Once the console is open, type `debug` and press Enter. If it prints your character's name, the install worked.

---

## Commands

Type all commands into the UE4SS console.

### Health / Stamina

|Command / Key|What it does|
|-|-|
|`heal` or `Z`|Sets Health/Stamina to 99 / 0.99|
|`healstep` or `X`|Adds +20 health per press (caps at 100)|
|`Ctrl + H`|Toggles a loop that sets full health (100/1) every 100ms|
|`ammo \[amount]`|Adds ammo/value to the item in hand (default: 1)|

### Giving items

|Command|Gives|
|-|-|
|`det`|Detonator|
|`ac`|Access Card|
|`bat`|Battery (full)|
|`ce` `cg` `cy` `cb` `cw` `cr`|Container (empty, green, yellow, blue, white, red)|
|`rif \[variant]`|Rifle (default 20 ammo)|
|`smg \[variant]`|SMG (default 30 ammo)|
|`sg \[variant]`|Shotgun (default 10 ammo)|
|`ps \[variant]`|Pistol (default 12 ammo)|
|`rv \[variant]`|Revolver (default 6 ammo)|
|`sh \[variant]`|Shorty (default 4 ammo)|
|`knife`|Knife|
|`rez`|Defibrillator|
|`ck`|Cookie|
|`c4`|C4|
|`fuse`|Fuse|
|`screw`|Screwdriver|
|`vent`|Vent Filter|
|`disk`|Hard Drive|
|`tape`|Tape Roll|
|`salmon` `tuna` `cod` `shrimp`|The corresponding fish|
|`give <name> \[v1] \[v2]`|Generic command for items not listed above, or custom values|

Example: `rif 2` → gives a rifle with variant 2.

### Misc

|Command|What it does|
|-|-|
|`debug`|Prints your character's full name to the console (useful to confirm install worked)|

---

## Troubleshooting

**Game crashes on startup:**
This script doesn't use event hooks (no god mode, no automatic death/item event listeners), so it shouldn't cause startup crashes. If it still happens, make sure your UE4SS build matches the game's current version.

**Getting "Unknown item" or "Asset not found" when running a command:**
The game may have received an update that changed the item's asset path. In that case the `ItemMap` table in `main.lua` needs updating.

**F10 doesn't open the console:**
Try `~` (tilde). If that still doesn't work, check your laptop's F-Lock/Fn setting.

**Items don't work but heal does:**
The `Set Hand Item` / `Net Take Item` function names may have changed in a game update — the script would need updating in that case.

---

## Disclaimer

This tool was built for educational/hobby purposes. Use is entirely at your own risk. Using it without others' consent may violate the game's rules and could get your account banned.

