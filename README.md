# Medicine Label Detection and Recognition

An automated computer vision pipeline that detects medicine boxes and extracts the medicine names. The system utilizes YOLOv8 to locate the packaging and EasyOCR to read the specific label text, outputting results with a custom, high-contrast overlay.

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![Ultralytics](https://img.shields.io/badge/Ultralytics_YOLOv8-000000?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)

## Core Features

* **Targeted Detection:** Uses a custom-trained YOLOv8 nano model to isolate medicine packaging within complex backgrounds.
* **Focused OCR Extraction:** Crops the detected region before passing it to EasyOCR to prevent background text interference and ensure high accuracy.
* **Video and Image Support:** Processes static images and frame-by-frame video files.
* **Premium Visual Output:** Renders anti-aliased bright yellow text on a dark semi-transparent card, combined with a translucent green bounding box fill for clear visibility.

## Pipeline Overview

1. **Frame Input:** The image or video frame is loaded and converted to the correct color space (RGB for OCR/Detection, BGR for OpenCV rendering)
2. **Object Detection:** YOLOv8 scans the frame and returns the exact coordinates of the medicine label
3. **Cropping:** The identified bounding box region is extracted from the original image
4. **Text Recognition:** EasyOCR reads the text strictly from the cropped section
5. **Rendering:** OpenCV creates a transparent overlay, draws the filled bounding box, generates the dark text card, and applies the recognized text back onto the original frame

## Installation

Ensure you have a Python environment set up, preferably within Kaggle or Google Colab. Install the required dependencies:

```bash
pip install ultralytics easyocr opencv-python matplotlib numpy
