# ml-notebooks

This repository holds Jupyter notebooks from [TigreGotico](https://tigregotico.pt) and the Open Voice OS community. The notebooks build datasets and train models for text-to-speech (TTS), wake word detection, and intent classification with open-source tools.

## Repository structure

### Text-to-speech (TTS)

Located in `/tts`. These notebooks create datasets and train VITS-based models.

| Notebook | Description |
| :--- | :--- |
| `tts_dataset_gen.ipynb` | Builds LJSpeech-style datasets from a single donor TTS voice with voice conversion (VC). The pipeline covers synthesis, super-resolution, silence trimming, and metadata generation. |
| `asr2tts.ipynb` | Converts in-the-wild ASR datasets, such as Mozilla Common Voice, into TTS training data. Steps include format standardization, denoising with `resemble-enhance`, silence trimming, volume normalization, and filtering by words per minute. |
| `train_vits.ipynb` | Trains and exports VITS models on Colab, Kaggle, or a local machine, using [phoonnx](https://github.com/TigreGotico/phoonnx). Supports fine-tuning and multi-speaker training, and exports to ONNX for Piper, Sherpa-ONNX, and OVOS. |

### Wake word (WW)

Located in `/ww`. This notebook generates synthetic wake word data so you can train a model without recording your own voice.

| Notebook | Description |
| :--- | :--- |
| `tts2ww.ipynb` | Generates positive and negative wake word samples. It creates adversarial samples with LLMs and grapheme edits to produce similar-sounding words, then applies TTS synthesis, voice cloning augmentation, and environment augmentation (noise, reverb). |

### Intent classification (M2V)

Located in `/m2v`. This notebook trains multilingual intent classifiers for offline voice assistants.

| Notebook | Description |
| :--- | :--- |
| `ovos_intent_classifier_multilingual.ipynb` | Trains intent classifiers with `model2vec` on the Open Voice OS intents dataset, then exports the model to ONNX. The exported model needs only `numpy` and `onnxruntime` to run. |

### Text utilities

Located in `/arabic_diacritics`.

| Notebook | Description |
| :--- | :--- |
| `lstm.ipynb` | Trains an LSTM model that adds diacritics to Arabic text, a preprocessing step for Arabic TTS models, and exports it to ONNX. |

## Getting started

Each notebook defines its own dependencies and installation steps in its first few cells.

Prerequisites:

1. Python 3.10 or later.
2. A GPU with CUDA support. Inference can run on CPU, but training (VITS) and heavy data processing (voice conversion, denoising) run faster with an NVIDIA GPU.
3. A Hugging Face account. Some notebooks need a token to upload datasets or download gated models.

To use a notebook:

1. Clone this repository:
   ```bash
   git clone https://github.com/TigreGotico/ml-notebooks
   cd ml-notebooks
   ```
2. Start Jupyter Lab or Notebook:
   ```bash
   jupyter lab
   ```
3. Open the notebook you need and follow the configuration cells at the top to set your paths and parameters.

## Related projects

* [TigreGotico/phoonnx](https://github.com/TigreGotico/phoonnx) — TTS engine used by `train_vits.ipynb` to train and export VITS models.
* [TigreGotico/chatterbox-onnx](https://github.com/TigreGotico/chatterbox-onnx) — voice cloning and TTS runtime used in the dataset generation pipelines.

## Community

These notebooks support the Open Voice OS ecosystem and the wider privacy-focused voice AI community.

* Open Voice OS: [openvoiceos.org](https://openvoiceos.org)
* Matrix chat: `#openvoiceos:matrix.org`

## Credits

Generative AI was used to convert some Python scripts into notebook format.

* Author: [TigreGotico](https://tigregotico.pt)
* Core technologies: [phoonnx](https://github.com/TigreGotico/phoonnx) (VITS), [chatterbox-onnx](https://github.com/TigreGotico/chatterbox-onnx), [Model2Vec](https://github.com/Minishlab/model2vec), [ONNX Runtime](https://onnxruntime.ai/)

## License

[Apache 2.0](LICENSE). See individual notebooks for any additional licensing details.
