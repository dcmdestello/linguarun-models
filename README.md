# Linguarun models

Parts-of-speech tagging models for [Linguarun](https://linguarun.com). The app
downloads them from this repository's releases the first time they're needed;
you don't need to fetch anything from here by hand.

## Contents

Each release (e.g. `models-v1`) holds one bundle per language, as flat assets
named `<language>-<file>`:

| Language | Code | Treebank   | Size    |
| -------- | ---- | ---------- | ------- |
| Catalan  | `ca` | UD AnCora  | 136 MB  |
| Spanish  | `es` | UD AnCora  | 136 MB  |
| English  | `en` | UD EWT     | 134 MB  |

| File             | What it is                                                       |
| ---------------- | ---------------------------------------------------------------- |
| `model.onnx`     | XLM-RoBERTa base tagger, vocabulary pruned, int8-quantized       |
| `tokenizer.json` | The matching (pruned) tokenizer                                  |
| `labels.json`    | Output labels (UD part-of-speech tags and features)              |
| `lexicon.tsv.gz` | Lemma lookup table                                               |
| `bundle.json`    | Bundle metadata, with each file's SHA-256 and size               |

The app pins every file's SHA-256 and size, so assets in a published release
must never be replaced; a new version of a model goes in a new release.

## Sources

- Models: fine-tuned from
  [`wietsedv/xlm-roberta-base-ft-udpos28-{ca,es,en}`](https://huggingface.co/wietsedv/xlm-roberta-base-ft-udpos28-ca)
  (Apache-2.0), with the vocabulary pruned to the target language and
  dynamically quantized to int8 with ONNX Runtime.
- Lexicons: built from the training sets of
  [UD Catalan-AnCora](https://github.com/UniversalDependencies/UD_Catalan-AnCora) and
  [UD Spanish-AnCora](https://github.com/UniversalDependencies/UD_Spanish-AnCora) (CC BY 4.0),
  [UD English-EWT](https://github.com/UniversalDependencies/UD_English-EWT) (CC BY-SA 4.0),
  and [michmech/lemmatization-lists](https://github.com/michmech/lemmatization-lists) (ODbL).

## Licence

To be decided. Until then, each component keeps the licence of its source,
listed above.
