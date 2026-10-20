# DQMJ3P Unobtainable monster synthesis

## General information

This is a RomFS patch that makes all unobtainable monsters of DQMJ3P available through synthesis, so geting these monsters won't requires cheats, plugins, or other out-of-game manipulations (besides installing this patch)

Unlike cheats and plugins, this patch should work regardless of other mods, like translations (as long as these other mods don't change or overwrite files from this patch).

I didn't use any AI, I went and read through a bunch of hex values of the various game files to guess what they mean to make this patch.

### Installation

> In any case, having DQMJ3P and its 1.3 update is required for this patch to work as intended.

- On emulator (Azahar is the recommended one)
  1. Get `DQMJ3PUMS.zip` from the [releases](https://github.com/Enignmeman/DQMJ3P-Unobtainable-monster-synthesis/releases/)
  2. Unzip it
  3. In the game list, right-click DQMJ3P and choose `Open Mods Location`
  4. Copy the `/romfs/` folder from the extracted archive to the just opened folder window
  5. The patch is installed, you can play the game now :smile:

- On a 3ds with CFW (Luma3DS)

> Don't forget to make sure you have game patching enabled.

  1. Get `DQMJ3PUMS.zip` from the [releases](https://github.com/Enignmeman/DQMJ3P-Unobtainable-monster-synthesis/releases/)
  2. Unzip it
  3. On your SD card, if they don't exist yet, create a `titles` folder in `/luma/` and a `00040000001ACB00` folder in `/luma/titles/` on your SD card
    - You should have `/luma/titles/00040000001ACB00` now
  4. Copy the `/romfs/` folder from the extracted archive to `/luma/titles/00040000001ACB00`
  5. The patch is installed, you can play the game now :smile:

## Technical information

> All of these files are in little-endian form, so the value `01 00` for example means 1 in decimal and the value `00 01` means 256 in decimal.

### `CouplingCourtRankParam.tp`

This file contains information regarding the synthesis options (or lack of).

Each data block after the 4 bytes-long header is made of 4 bytes:
- 2 bytes for synthesis status
- 2 bytes for monster species ID

Synthesis status can be 4 different values:

|Value|Meaning|
| --- | --- |
|0|Can be acquired through "generic synthesis"|
|1|Can be acquired through "special synthesis"[^1]|
|2|Can be acquired through both "generic synthesis" and "special synthesis"[^2]|
|3|Cannot be acquired through synthesis|

[^1]: Requires a special synthesis recipe to exist, else will act like no synthesis is available.
[^2]: Will act like "generic synthesis" if no special synthesis recipe exists

#### Monsters made available:

|Offset|Monster name|
| --- | --- |
|778|Premium Slime|
|9BC|King Healslime|
|B48|Gome-Chan|
|5AC|Dimensional Dragon|
|AB0|Halcyon The Godsteed|
|854|Bebingo Satan|
|A08|Sagittar|
|790|Master CPU Q484|
|AC4|God/Numen|
|A48|Dark Lord Valaat|
|89C|Kandar ladies|
|A14|Rugius|
|A10|Vera|
|B14|Timelord Omega Rolex|
|A24|Aldarahla|
|7A4|Leokid|
|798|Tiko|
|79C|Krilly|
|498|Chibi One-Twos|
|49C|Chibi Threes|
|4A0|Chibi Fours|
|770|Chibi Eights|
|908|J3-Rebel Axel|
|900|J3-Rebel Wing|
|904|J3-Rebel Marine|
|614|Rebjorn|
|618|Starkers|
|61C|Zoma's Little Devil|
|610|Slider kids|
|784|Slider Girl|
|77C|Ultra Slime/Slider Hero|
|780|Nemeslime/Slider Dark|

### `Coupling4Param.tp`

This file contains information regarding the 4-monster synthesis recipes.

Each data block after the 4 bytes-long header is made of 10 bytes:
- 2 bytes for the monster species ID of the result
- 4\*2 bytes for each of the 4 monster species IDs of the components to synth together

IDs don't require any particular order

#### Added 4-monster synthesis recipes:

|Monster name|4-monster synthesis recipe|
| --- | --- |
|King Healslime|Healslime + Emperor Slime + Fledgling Card + Gome-Chan|
|Halcyon the Godsteed/Godlike|Godsteed + Godsteed + Godsteed + Godsteed|
|Sagittar|Ultimate Weapon + Killer Crimson + Totem of Urubea + Master CPU Q484|
|Master CPU Q484|J3P Axel Gold + J3P Wing Gold + J3P Marin Gold + Gold Nochoro Z|
|God/Numen|Demonking Orgodemir + King Healslime + Rottney + Elder/Grandpa Pipit|
|Kandar Ladies|Kandar + Queen Ferz + Mystic Juliante + Krilly|

 
 ## Changelog

Version 0
 - Made listed monsters available through generic synthesis, I don't know how the generic synthesis algorythm works, so expect ridiculous/expensive synthesis recipes to get some monsters.
 - Created somewhat basic documentation regarding the files that were modified.
Version 0.1
 - Monsters on the new list are now available through special synthesis, the corresponding 4-monster synthesis to obtain them is listed too.
   - These 4-monster recipes were made and reviewed with members of the community.
 - Updated documentation with new findings.
 