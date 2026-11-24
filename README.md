# Manuscribe's recognition models

The files Manuscribe fetches to read manuscript pages in the browser: a line segmenter, a line recogniser for
Devanagari manuscripts and a word spacer for Sanskrit, in ONNX, with the parameters of the steps between them, and
ONNX Runtime Web to run them. Manuscribe (Settings › Recognition) reads `index.json`, fetches the newest pack it can
read and the runtime the browser needs, checks every file's SHA-256 against the manifest, and keeps them in the
browser; recognition then runs on the device, offline, and nothing is sent anywhere.

- `index.json`: the packs and runtimes on this site.
- `packs/<pack>/`: a pack, its `manifest.json` (every file's checksum, the inputs and outputs of each network, what
  each model learned from) and `MODEL_CARD.md`.
- `runtime/onnxruntime-web-<version>/`: ONNX Runtime Web's files as published on npm, unchanged (MIT licence).
- `contribute.json`: where Manuscribe sends corrected lines that their editors agree to contribute for training (an
  issue in the inbox repository it names), and the public key it seals them to, so that only the maintainer can open
  them.

The packs are made by [devanagari-manuscript-ocr](https://github.com/drdhaval2785/devanagari-manuscript-ocr) (`python -m msocr.export_onnx`, then
`python -m msocr.site`); its reference pipeline in Python and Manuscribe's JavaScript are held to give the same output
by stage fixtures. Made with devanagari-manuscript-ocr 0.13.1, for Manuscribe 0.13.1.

Licences: the models' weights are under CC BY-SA 4.0 (see LICENSE.md); ONNX Runtime Web under MIT
(runtime/*/LICENSE).
