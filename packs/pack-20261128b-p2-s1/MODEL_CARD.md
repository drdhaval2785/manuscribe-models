# pack-20261128b-p2-s1

A recognition pack for Manuscribe: the line segmenter, the line recogniser and the word spacer, with the parameters of the stages between them (pipeline version 2, spacer version 1). Weights: segmenter, recogniser, language model CC BY-NC-SA 4.0; spacer CC BY-SA 4.0. Made with devanagari-manuscript-ocr 0.13.5 (https://github.com/drdhaval2785/devanagari-manuscript-ocr).

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

Characters: 90. Trained, run after run:

- `run4` on LDII_85885, 4509 lines, cut from the U-Net's segmentation as Manuscribe cuts them
- `ft6` on LDII_19634, 685 lines, cut from the U-Net's segmentation as Manuscribe cuts them
- `pool1` on 6 manuscripts at once, each given the same share of every pass: LDII_1806, LDII_19634, LDII_45364, LDII_82668, LDII_85885, LDII_9851, cut from the U-Net's segmentation as Manuscribe cuts them
- `pool2` on 10 manuscripts at once, each given the same share of every pass: LDII_1806, LDII_19634, LDII_4278, LDII_45364, LDII_6487, LDII_80136, LDII_82320, LDII_82668, LDII_85885, LDII_9851, cut from the U-Net's segmentation as Manuscribe cuts them
- `pool3` on 18 manuscripts at once, each given the same share of every pass: LDII_1806, LDII_19634, LDII_4278, LDII_45364, LDII_6487, LDII_80136, LDII_82320, LDII_82668, LDII_85885, LDII_9851, RTJ_1127, RTJ_1307, RTJ_4387, RTJ_4894, RTJ_4914, RTJ_6025, UPSS_1322, UPSS_2042, cut from the U-Net's segmentation as Manuscribe cuts them
- `pool3b` on 18 manuscripts at once, each given the same share of every pass: LDII_1806, LDII_19634, LDII_4278, LDII_45364, LDII_6487, LDII_80136, LDII_82320, LDII_82668, LDII_85885, LDII_9851, RTJ_1127, RTJ_1307, RTJ_4387, RTJ_4894, RTJ_4914, RTJ_6025, UPSS_1322, UPSS_2042, cut from the U-Net's segmentation as Manuscribe cuts them
- `pool4` on 37 manuscripts at once, each given the same share of every pass: LDII_1806, LDII_19634, LDII_4278, LDII_45364, LDII_6487, LDII_80136, LDII_82320, LDII_82668, LDII_85885, LDII_9851, RTJ_1065, RTJ_1127, RTJ_1307, RTJ_1309, RTJ_1406, RTJ_1633, RTJ_4078, RTJ_4387, RTJ_4740, RTJ_4818, RTJ_4826, RTJ_4853, RTJ_4858, RTJ_4894, RTJ_4913, RTJ_4914, RTJ_4930, RTJ_4966, RTJ_4972, RTJ_5294, RTJ_5295, RTJ_5520, RTJ_5605, RTJ_5753, RTJ_6025, UPSS_1322, UPSS_2042, cut from the U-Net's segmentation as Manuscribe cuts them
- `pool4b` on 37 manuscripts at once, each given the same share of every pass: LDII_1806, LDII_19634, LDII_4278, LDII_45364, LDII_6487, LDII_80136, LDII_82320, LDII_82668, LDII_85885, LDII_9851, RTJ_1065, RTJ_1127, RTJ_1307, RTJ_1309, RTJ_1406, RTJ_1633, RTJ_4078, RTJ_4387, RTJ_4740, RTJ_4818, RTJ_4826, RTJ_4853, RTJ_4858, RTJ_4894, RTJ_4913, RTJ_4914, RTJ_4930, RTJ_4966, RTJ_4972, RTJ_5294, RTJ_5295, RTJ_5520, RTJ_5605, RTJ_5753, RTJ_6025, UPSS_1322, UPSS_2042, cut from the U-Net's segmentation as Manuscribe cuts them

The transcriptions of RTJ_1065 (paramahaṃsapaddati, e-text M00664), RTJ_1127 (svAtantryadIpikA, e-text M00668), RTJ_1307 (zrIgurustutiratnAvalI, e-text M00653), RTJ_1309 (vāñchākalpalatā, e-text M00641), RTJ_1406 (mudrāprakāśa, e-text M00627), RTJ_1633 (dakṣiṇāmūrtisaṃhitā, e-text M00625), RTJ_4078 (kaumārasaṃhitā, e-text M00661), RTJ_4387 (mRgendravRtti, e-text M00663), RTJ_4740 (ramārcanacandrikā, e-text M00665), RTJ_4818 (navārṇavacaṇḍipañjāṅga, e-text M00628), RTJ_4826 (tripurabhairavīpañcāṅga, e-text M00637), RTJ_4853 (mantracandrikā, e-text M00635), RTJ_4858 (mātṛkārṇanighaṇṭu, e-text M00626), RTJ_4894 (UrdhvAmnAya, e-text M00640), RTJ_4913 (dattātreyatantra, e-text M00632), RTJ_4914 (AgamakalpalatA, e-text M00659), RTJ_4930 (tārābhaktitaraṅgiṇī, e-text M00636), RTJ_4966 (ajñānadhvāntadīpikā, e-text M00622), RTJ_4972 (tārāsahasranāmavyākhyābhidhārthacintāmaṇi, e-text M00638), RTJ_5294 (agastyasaMhitA, e-text M00574), RTJ_5295 (kātyāyanītantraṭīka, e-text M00631), RTJ_5520 (ānandeśvarapaddhatiḥ, e-text M00624), RTJ_5605 (kaulārcanadīpikā śrījñānatantra, e-text M00633), RTJ_5753 (tripurasundarīsahasranāmastotra, e-text M00639), RTJ_6025 (bagalAmukhIpaJcAGgam, e-text M00623), UPSS_1322 (parAmbArcanacandrikA, e-text M00629), UPSS_2042 (tatvazodhanam, e-text M00655) are Muktabodha Indological Research Institute's diplomatic e-texts (muktabodha.org, CC BY-NC 4.0), typed from eGangotri's scans of manuscripts of the Shri Raghunath Temple MSS Library, Jammu (RTJ) and the Uttar Pradesh Sanskrit Sansthan, Lucknow (UPSS); their lines were paired with the scans' rows by devanagari-manuscript-ocr's msocr/muktabodha.py (for RTJ_1065, RTJ_1309, RTJ_1406, RTJ_1633, RTJ_4078, RTJ_4740, RTJ_4818, RTJ_4826, RTJ_4853, RTJ_4858, RTJ_4913, RTJ_4930, RTJ_4966, RTJ_4972, RTJ_5295, RTJ_5520, RTJ_5605, RTJ_5753 the pages and lines were matched to the text by the MIDF/eGangotri dataset, huggingface.co/datasets/tadad/midf-egangotri-sanskrit, and brought in by msocr/midf.py). That is why this recogniser and the language model are under CC BY-NC-SA 4.0.

It reads the hands it learned from best; a hand it has never seen reads worse, the more so the further that hand is from these. Pooling over more hands is what makes it read new ones better.

## Word spacer

Run `full_e10_s1`, trained on Pramāṇa's open release: Sanskrit Wikisource (CC BY-SA), SARIT (CC BY-SA), Ambuda (CC0). Threshold 0.45.

## Language model

Lines are read with a character 6-gram language model: a prefix beam search over the recogniser's probabilities, each reading weighed by how its letters run in Sanskrit (alpha 0.4, beta 1.0, beam 16). Daṇḍas, digits and marks are one boundary symbol to it. Its parts, mixed by weight:

- `lexica` (weight 0.7): 16,059,845 letters of the lexica texts (115 works in IAST, 790,200 sentences); 2,072,531 n-grams, those seen under 3 times left out; 10.3 MB.
- `own` (weight 0.3): 2,724,001 letters of the manuscripts' own transcriptions (LDII_1806 68, LDII_19634 697, LDII_4278 44, LDII_45364 60, LDII_6487 60, LDII_80136 72, LDII_82320 60, LDII_82668 104, LDII_85885 4509, LDII_9851 52, RTJ_1065 98, RTJ_1127 710, RTJ_1307 115, RTJ_1309 157, RTJ_1406 340, RTJ_1633 2478, RTJ_4078 300, RTJ_4387 1792, RTJ_4740 1227, RTJ_4818 1114, RTJ_4826 1058, RTJ_4853 1230, RTJ_4858 82, RTJ_4894 372, RTJ_4913 159, RTJ_4914 7403, RTJ_4930 1336, RTJ_4966 825, RTJ_4972 2110, RTJ_5294 736, RTJ_5295 226, RTJ_5520 5956, RTJ_5605 951, RTJ_5753 252, RTJ_6025 922, UPSS_1322 924, UPSS_2042 52 lines); 2,359,148 n-grams; 11.6 MB.

Measured on lines never trained on: 2026-11-26, the pooled recogniser pool2 on the last page of each of its ten manuscripts, a quarter fewer character errors (3.79 % to 2.85 %) and three tenths fewer akṣara errors (6.18 % to 4.28 %) than reading letter by letter; 2026-11-27, pool3b on held-out test pages, LDII_85885 2.77 % to 2.31 %, RTJ_4387 3.41 % to 2.58 %, RTJ_4914 4.81 % to 3.21 %, RTJ_1127 2.40 % to 1.78 % of characters wrong. Daṇḍas and digits are not its business.

## Consent

No contributed data: the segmenter and the recogniser learned from the developer's own manuscripts only.

Language and script: sa-Deva only. Lines and pages of another language or script are never mixed into these models' training.
