# TigreGotico Open Voice Notebooks

**Empowering the FOSS community to train, fine-tune, and deploy state-of-the-art voice models.**

This repository contains a collection of Jupyter notebooks developed by [TigreGotico](https://tigregotico.pt) and the Open Voice OS community. These tools are designed to democratize access to voice AI technologies, allowing developers to create datasets and train models for Text-to-Speech (TTS), Wake Word detection, and Intent Classification using open-source tools.

## 📂 Repository Structure

### 🗣️ Text-to-Speech (TTS)
*Located in `/tts`*

Tools for creating datasets and training VITS-based models.

| Notebook | Description |
| :--- | :--- |
| **`tts_dataset_gen.ipynb`** | **Synthetic TTS Dataset Generator.** Creates LJSpeech-style datasets using a single "donor" TTS voice and Voice Conversion (VC). Features a full pipeline: synthesis, super-resolution, silence trimming, and metadata generation. |
| **`asr2tts.ipynb`** | **ASR-to-TTS Pipeline.** Converts "in-the-wild" ASR datasets (like Mozilla Common Voice) into high-quality TTS training data. Includes format standardization, denoising (`resemble-enhance`), silence trimming, volume normalization, and WPM filtering. |
| **`train_vits.ipynb`** | **Train & Export VITS.** A platform-agnostic notebook (Colab, Kaggle, Local) to train models using [phoonnx](https://github.com/TigreGotico/phoonnx). Supports fine-tuning, multi-speaker training, and exporting to ONNX for use with Piper, Sherpa-ONNX, and OVOS. |

### 🔔 Wake Word (WW)
*Located in `/ww`*

Tools for generating synthetic wake word data to bootstrap training without user recordings.

| Notebook | Description |
| :--- | :--- |
| **`tts2ww.ipynb`** | **Wake Word Dataset Generator.** A comprehensive pipeline that generates positive and negative samples. Features **adversarial generation** (using LLMs and grapheme edits to create similar-sounding words), TTS synthesis, voice cloning augmentation, and environmental augmentation (noise/reverb) for robust model training. |

### 🧠 Intent Classification (M2V)
*Located in `/m2v`*

Efficient, multilingual intent recognition for offline voice assistants.

| Notebook | Description |
| :--- | :--- |
| **`ovos_intent_classifier_multilingual.ipynb`** | **Multilingual Intent Classifier.** Trains extremely efficient classifiers using `model2vec` on the Open Voice OS intents dataset. Includes steps to export the model to ONNX for **dependency-free inference** (requiring only `numpy` and `onnxruntime`). |

### 📝 Text Utilities
*Located in `/arabic_diacritics`*

| Notebook | Description |
| :--- | :--- |
| **`lstm.ipynb`** | **Arabic Diacritizer.** Trains a lightweight LSTM model to automatically add diacritics to Arabic text. This is a critical preprocessing step for training high-quality Arabic TTS models. Includes export to ONNX. |

---

## 🚀 Getting Started

These notebooks are designed to be self-contained. Most define their own dependencies and installation steps within the first few cells.

**Prerequisites:**
1.  **Python 3.10+** (Recommended).
2.  **GPU Acceleration:** While inference steps can run on CPU, training (VITS) and heavy data processing (Voice Conversion/Denoising) are significantly faster with an NVIDIA GPU (CUDA).
3.  **HuggingFace Account:** Some notebooks require a token to upload datasets or download gated models.

**Usage:**
1.  Clone this repository:
    ```bash
    git clone <your-repo-url>
    cd <your-repo-name>
    ```
2.  Launch Jupyter Lab or Notebook:
    ```bash
    jupyter lab
    ```
3.  Open the desired notebook and follow the "Configuration" cells at the top of each file to set your paths and parameters.

---

## 🤝 Community & Support

These tools are built to support the **Open Voice OS** ecosystem and the broader privacy-focused AI community.

* **Open Voice OS:** [openvoiceos.org](https://openvoiceos.org)
* **Matrix Chat:** `#openvoiceos:matrix.org`

## 📜 Credits & Acknowledgments

> **DISCLAIMER**: Generative AI was used to convert various python scripts into notebook format

* **Author:** [TigreGotico](https://tigregotico.pt)
* **Core Technologies:**
    * [Phoonnx](https://github.com/TigreGotico/phoonnx) / VITS
    * [chatterbox-onnx](https://github.com/TigreGotico/chatterbox-onnx)
    * [Model2Vec](https://github.com/Minishlab/model2vec)
    * [ONNX Runtime](https://onnxruntime.ai/)

## ⚖️ License

[Apache 2.0](LICENSE) (or see individual notebooks for specific licensing details).
