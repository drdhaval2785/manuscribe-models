# Licences

The models' weights in `packs/` (the segmenter, the recogniser, the language model and the word spacer, and the
parameter files beside them) are licensed per model; each pack's `manifest.json` gives the licence of each, and its
`MODEL_CARD.md` says what each learned from.

- Packs made from 27 November 2026 on: the segmenter, the recogniser and the language model under the Creative Commons
  Attribution-NonCommercial-ShareAlike 4.0 International licence (CC BY-NC-SA 4.0,
  https://creativecommons.org/licenses/by-nc-sa/4.0/), because they may learn from manuscripts whose transcriptions
  are under CC BY-NC 4.0 (Muktabodha Indological Research Institute's diplomatic e-texts); the word spacer under the
  Creative Commons Attribution-ShareAlike 4.0 International licence (CC BY-SA 4.0,
  https://creativecommons.org/licenses/by-sa/4.0/), because it learns from Sanskrit Wikisource and SARIT (CC BY-SA)
  and Ambuda (CC0) through Pramāṇa's open release.
- Packs made before that date (pack-20261124-p1-s1, pack-20261124b-p1-s1, pack-20261126-p2-s1): every model under
  CC BY-SA 4.0, as they were published.

ONNX Runtime Web, in `runtime/`, is Microsoft's, under the MIT licence: see the LICENSE file beside it.
