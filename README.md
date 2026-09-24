# 🖼️ AI Image Classifier

![Python](https://img.shields.io/badge/python-3.9%2B-blue)
![Streamlit](https://img.shields.io/badge/streamlit-app-FF4B4B)
![License](https://img.shields.io/badge/license-MIT-green)

A simple, browser-based image classification app built with **Streamlit** and a pre-trained **MobileNetV2** convolutional neural network. Upload any image and get the model's top 3 predictions with confidence scores — no training or GPU required.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [How It Works](#how-it-works)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Possible Improvements](#possible-improvements)
- [License](#license)

## Overview

This app uses [MobileNetV2](https://arxiv.org/abs/1801.04381), a lightweight convolutional neural network pre-trained on [ImageNet](https://www.image-net.org/) (1.4M images across 1,000 categories). It's a great starting point for learning how pre-trained models and simple web UIs fit together — the whole pipeline, from upload to prediction, runs in under 100 lines of Python.

## Features

- 📤 Drag-and-drop image upload (JPG, JPEG, PNG)
- 🧠 Classification powered by MobileNetV2, pre-trained on ImageNet's 1,000 classes
- 🏆 Displays the top 3 predicted labels with confidence percentages
- ⚡ Model is cached with `@st.cache_resource` so it only loads once per session, not on every prediction
- 🖥️ Clean, minimal UI with no configuration needed beyond `pip install`

## How It Works

1. The user uploads an image through Streamlit's file uploader.
2. The image is converted to a NumPy array and resized to 224×224 pixels — the input size MobileNetV2 expects.
3. Pixel values are normalized using MobileNetV2's own `preprocess_input` function.
4. The processed image is passed through the pre-trained model to get raw predictions.
5. `decode_predictions` converts the raw output into human-readable labels with confidence scores.
6. The top 3 results are displayed in the app.

## Installation

```bash
# Clone the repository
git clone https://github.com/<Codymur>/ai-image-classifier.git
cd ai-image-classifier

# Create and activate a virtual environment (recommended)
python -m venv venv
source venv/bin/activate      # on Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Usage

```bash
streamlit run ImageClassifierScript.py
```

Streamlit will open the app in your browser (usually at `http://localhost:8501`). Upload an image, click **Classify Image**, and view the top 3 predictions.

## Project Structure

```
ai-image-classifier/
├── ImageClassifierScript.py             # Main Streamlit application
├── requirements.txt   # Python dependencies
├── .gitignore
└── README.md
```

## Possible Improvements

- Show prediction confidences as a bar chart instead of plain text
- Support batch classification of multiple images at once
- Let users pick between different pre-trained models (ResNet, EfficientNet, etc.)
- Deploy the app publicly (Streamlit Community Cloud or Hugging Face Spaces)
- Fine-tune on a custom dataset to classify categories outside the 1,000 ImageNet classes

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT) — feel free to use, modify, and learn from it.

---

Built by Seymur Shiriyev as a first hands-on project working with pre-trained deep learning models.
