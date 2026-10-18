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
|778|premium slime|
|9BC|king healslime|
|B48|gome-chan|
|5AC|dimensional dragon|
|AB0|halcyon the godsteed|
|854|bebingo satan|
|A08|sagittar|
|790|master cpu q484|
|AC4|god/numen|
|A48|dark lord valaat|
|89C|kandar ladies|
|A14|rugius|
|A10|vera|
|B14|timelord omega rolex|
|A24|aldarahla|
|   |
|7A4|leokid|
|798|tiko|
|79C|kirlly|
|   |
|498|chibi one-twos|
|49C|chibi threes|
|4A0|chibi fours|
|770|chibi eights|
|   |
|908|j3-rebel axel|
|900|j3-rebel wing|
|904|j3-rebel marine|
|   |
|614|rebjorn|
|618|starkers|
|61C|zoma's little devil|
|610|slider kids|
|   |
|784|slider girl|
|77C|ultra slime|
|780|nemeslime|

## Changelog

Version 0
 - made listed monsters available through generic synthesis, I don't know how the generic synthesis algorythm works, so expect ridiculous/expensive synthesis recipes to get some monsters.