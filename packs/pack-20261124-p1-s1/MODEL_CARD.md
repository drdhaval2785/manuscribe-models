# pack-20261124-p1-s1

A recognition pack for Manuscribe: the line segmenter, the line recogniser and the word spacer, with the parameters of the stages between them (pipeline version 1, spacer version 1). Weights under CC BY-SA 4.0. Made with devanagari-manuscript-ocr 0.12.0 (https://github.com/drdhaval2785/devanagari-manuscript-ocr).

## Segmenter

Run `tseg1`. [tseg] run tseg1: train 2929 pages, val 129, test 209; 237 pages left out because Kraken's segmentation of them is doubtful (data/tseg/flagged_pages.tsv); device mps

Trained on pages of these manuscripts (pages each, 2919 in all, as the training split stands at this pack's build; the run's log above gives the split it was trained on):

- AKGM_0025383: 189
- LDII_15152: 42
- LDII_17963: 214
- LDII_1806: 148
- LDII_19634: 321
- LDII_22995: 24
- LDII_24075: 22
- LDII_24083: 25
- LDII_24140: 64
- LDII_3746: 182
- LDII_38386: 130
- LDII_4278: 116
- LDII_45071: 116
- LDII_45364: 121
- LDII_6487: 76
- LDII_7105: 226
- LDII_80136: 56
- LDII_82320: 139
- LDII_82328: 180
- LDII_82668: 123
- LDII_85885: 258
- LDII_9851: 147

Training images are 608–756 px high (median 685); Manuscribe renders a side at about the median.

## Recogniser

Characters: 81. Trained, run after run:

- `run3` on LDII_85885, 4218 lines
- `ft4` on LDII_19634, 445 lines

It reads the hands it learned from well and other hands poorly: a model pooled over many hands is to replace it.

## Word spacer

Run `full_e10_s1`, trained on Pramāṇa's open release: Sanskrit Wikisource (CC BY-SA), SARIT (CC BY-SA), Ambuda (CC0). Threshold 0.45.

## Consent

No contributed data: the segmenter and the recogniser learned from the developer's own manuscripts only.

Language and script: sa-Deva only. Lines and pages of another language or script are never mixed into these models' training.
