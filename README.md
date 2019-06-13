# tessdata_fast – Fast integer versions of trained models

This repository contains fast integer versions of trained models for the [Tesseract Open Source OCR Engine](https://github.com/tesseract-ocr/tesseract).

These models only work with the LSTM OCR engine of Tesseract 4.

- These are a speed/accuracy compromise as to what offered the best "value for money" in speed vs accuracy. 
- For some languages, this is still best, but for most not. 
- The "best value for money" network configuration was then integerized for further speed.
- Most users will want to use these traineddata files to do OCR and these will be shipped as part of Linux distributions eg. Ubuntu 18.04.
- Fine tuning/incremental training will **NOT** be possible from these `fast` models, as they are 8-bit integer. 
- When using the models in this repository, only the new LSTM-based OCR engine is supported. The legacy `tesseract` engine is not supported with these files, so Tesseract's oem modes '0' and '2' won't work with them.

## Two types of models

The repository contains two types of models,
- those for a single language and
- those for a single script supporting one or more languages.

Most of the script models include English training data as well as the script, but not **Cyrillic**, as that would have a major ambiguity problem. 

On Debian and Ubuntu, the language based traineddata packages are named `tesseract-ocr-LANG` where LANG is the three letter language code eg. tesseract-ocr-eng (English language), tesseract-ocr-hin (Hindi language), etc. 

On Debian and Ubuntu, the script based traineddata packages are named `tesseract-ocr-script-SCRIPT` where SCRIPT is the four letter script code eg. tesseract-ocr-script-latn (Latin Script), tesseract-ocr-script-deva (Devanagari Script), etc. 

### Data files for a particular script

Initial capitals in the filename indicate the one model for all languages in that script. These are now available under script subdirectory.

- **Latin** is all latin-based languages, except vie.
- **Vietnamese** is for latin-based Vietnamese language.
- **Fraktur** is basically a combination of all the latin-based languages that have an 'old' variant.
- **Devanagari** is for hin+san+mar+nep+eng.

### LSTM training details for different languages and scripts

For Latin-based languages, the existing model data provided has been trained on about 400000 textlines spanning about 4500 fonts. For other scripts, not so many fonts are available, but they have still been trained on a similar number of textlines.  eg. Latin ~4500 fonts, Devanagari ~50 fonts, Kannada 15.

With a theory that poor accuracy on test data and over-fitting on training data was caused by the lack of fonts, the training data has been mixed with English, so that some of the font diversity might generalize to the other script. The overall effect was slightly positive, hence the script models include English language also.

### Example - jpn and  Japanese

**'jpn'** contains whatever appears on the www that is labelled as the language, trained only with fonts that can render Japanese. 

**Japanese** contains all the languages that use that script (in this case just the one) PLUS English.The resulting model is trained with a mix of both training sets, with the expectation that some of the generalization to 4500 English training fonts will also apply to the other script that has a lot less.

**'jpn_vert'** is trained on text rendered vertically (but the image is rotated so the long edge is still horizontal).

**'jpn'** loads **'jpn_vert'** as a secondary language so it can try it in case the text is rendered vertically. This seems to work most of the time as a reasonable solution.

--------------------------------

See the [Tesseract wiki](https://github.com/tesseract-ocr/tesseract/wiki/Data-Files) for additional information.

All data in the repository are licensed under the
Apache-2.0 License, see file [LICENSE](LICENSE).
