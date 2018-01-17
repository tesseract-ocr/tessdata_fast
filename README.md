# tessdata_fast – Fast integer versions of trained models

This repository contains fast integer versions of trained models for the
[Tesseract Open Source OCR Engine](https://github.com/tesseract-ocr/tesseract).

Most users will want to use these traineddata files and this is what is planned to be shipped as part of Linux distributions.

When using the models in this repository, only the new LSTM-based OCR engine is supported. The legacy 'tesseract' engine is not supported with these files, so Tesseract's oem modes '0' and '2' won't work with them.

Initial capitals indicate the one model for all languages in that script. 

Latin is all latin-based languages, 
except vie, which has its own Vietnamese.

Devanagari is hin+san+mar+nep+eng

Fraktur is basically a combination of all the latin-based languages that have an 'old' variant.

Most of the script models include English training data as well as the script, but not for Cyrillic, as that would have a major ambiguity problem. 

For Latin-based languages, the existing model data provided has been trained on about 400000 textlines spanning about 4500 fonts. For other scripts, not so many fonts are available, but they have still been trained on a similar number of textlines. `

For Latin, I have ~4500 fonts to train with. For Devanagari ~50, and for Kannada 15. With a theory that poor accuracy on test data and over-fitting on training data was caused by the lack of fonts, I tried mixing the training data with English, thinking that English is often mixed in anyway, and some of the font diversity might generalize to the other script. The overall effect was slightly positive, so I left it that way.

'jpn' contains whatever appears on the www that is labelled as the language, trained only with fonts that can render Japanese. As with most of the other Script traineddatas, 'Japanese' contains all the languages that use that script (in this case just the one) PLUS English.The resulting model is trained with a mix of both training sets, with the expectation that some of the generalization to 4500 English training fonts will also apply to the other script that has a lot less.

'jpn_vert' is trained on text rendered vertically (but the image is rotated so the long edge is still horizontal).

'jpn' loads 'jpn_vert' as a secondary language so it can try it in case the text is rendered vertically. This seems to work most of the time as a reasonable solution.

See the [Tesseract wiki](https://github.com/tesseract-ocr/tesseract/wiki/Data-Files)
for additional information.

All data in the repository are licensed under the
Apache-2.0 License, see file [COPYING](COPYING).
