# Arknights operator voice lines, Japanese (JP)

Game assets from Arknights, extracted from the **EN** game server. This repository is
generated and refreshed by machine; do not edit its contents by hand.

## What is here

Source: `audio/sound_beta_2/voice/**` on the EN game server.

One directory per voice pack. Operator packs are `char_<operator_id>/`, holding that operator's clips as `cn_001.mp3`, `cn_024.mp3` and so on. Non-operator packs are `extra_<n>/`.

The clip numbers are the game's own dialogue keys, so `char_002_amiya/cn_004.mp3` is what `charword_table.json` in ArknightsGameDataEN calls `CN_004`, and the folder name matches the `charId` used across that repository's tables.

## Format

MP3, 96 kbps mono

This is the set the game stores without a language suffix under `voice/`, which is the Japanese one. The other languages live in the sibling repositories `arknights-voice-cn`, `arknights-voice-en` and `arknights-voice-kr`.

## Updating

`.github/workflows/update.yml` runs once a day. Incremental state lives in
`.state/voice-jp.json`, so only bundles that are new or whose hash changed are downloaded
and extracted again; a rerun with nothing new is a no-op.

Run it locally:

```bash
python -m pip install "arkprts[all]" lameenc
python tools/assets_sync.py --out . --state .state
python tools/assets_sync.py --verify --out .
```

`tools/assets_sync.py` in this repository is a self-contained copy whose default group is
`voice-jp`. The canonical copy lives in [ArknightsGameDataEN](https://github.com/ThiagoVsky/ArknightsGameDataEN) under
`tools/assets_sync.py`; the download uses
[arkprts](https://github.com/thesadru/arkprts) and the extraction uses
[UnityPy](https://github.com/K0lb3/UnityPy) with the LZ4AK decompressor that arkprts
registers in place of the LZHAM that UnityPy does not implement.

