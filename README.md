# tessdata_fast – Fast integer versions of trained models

This repository contains fast integer versions of trained models for the
[Tesseract Open Source OCR Engine](https://github.com/tesseract-ocr/tesseract).

Most users will want to use these traineddata files and this is what is planned to be shipped as part of Linux distributions.

When using the models in this repository, only the new LSTM-based OCR engine is supported. The legacy 'tesseract' engine is not supported with these files, so Tesseract's oem modes '0' and '2' won't work with them.

Initial capitals indicate the one model for all languages in that script. Most of the script models include English training data as well as the script, but not for Cyrillic, as that would have a major ambiguity problem.

Latin is all latin-based languages, 
except vie, which has its own Vietnamese.

Devanagari is hin+san+mar+nep+eng

Fraktur is basically a combination of all the latin-based languages that have an 'old' variant.

See the [Tesseract wiki](https://github.com/tesseract-ocr/tesseract/wiki/Data-Files)
for additional information.

All data in the repository are licensed under the
Apache-2.0 License, see file [COPYING](COPYING).
