# Medicine Label Detection, Recognition and Automated Billing Pipeline

An advanced computer vision pipeline that detects medicine packaging, extracts label text via OCR, performs fuzzy database matching, and renders a real-time smart billing dashboard overlay onto videos. The system combines a custom-trained YOLOv8 nano model, EasyOCR, and a dynamic price-tracking database.

## Video Demo

[Watch the demo video](https://github.com/user-attachments/assets/8d9a8e99-f00f-47ad-a586-bb9a4a42524b)

## Tech Stack

* Python
* Jupyter Notebook
* PyTorch
* OpenCV
* NumPy
* Matplotlib

## Key Features

* **Targeted Detection:** Uses a custom YOLOv8 nano model to accurately locate medicine packaging within complex video frames.
* **Focused OCR Extraction:** Crops detected bounding box regions before passing them to EasyOCR to significantly minimize background noise and improve recognition accuracy.
* **Fuzzy Text Matching & Database Lookup:** Employs Python's `difflib` and substring fallback mechanisms to safely match imperfect OCR results against a predefined price database.
* **Real-Time Live Billing Dashboard:** Automatically compiles unique scanned medicines, itemizes individual prices, and computes a live grand total on the fly.
* **Non-Intrusive Bottom-Right UI:** Features a compact, semi-transparent dark-mode dashboard positioned cleanly at the bottom-right corner to prevent obstructing active video objects.
* **Video & Image Support:** Processes single frames or complete video streams frame-by-frame with robust codec management (with automatic fallback from `avc1` to `mp4v`).

## Pipeline Overview

1. **Frame Input:** Load a video frame and convert color channels as required.
2. **Object Detection:** YOLOv8 detects packaging boxes and returns spatial coordinates.
3. **Region Cropping:** Isolate the bounding box sub-image from the frame.
4. **Text Recognition:** Pass the cropped region to EasyOCR to extract raw text strings.
5. **Database Matching:** Query the price dictionary using fuzzy logic to retrieve clean item names and pricing.
6. **Dashboard & HUD Rendering:** Update the unique item dictionary, calculate running totals, and render both the localized bounding boxes and the bottom-right summary ledger.

## Use Cases

* **Smart Pharmacy Point of Sale (POS) / Checkout:** Automate retail billing counters where cashiers or automated conveyors pass medicine boxes through a camera view to instantly generate itemized bills.
* **Inventory Auditing & Stock Management:** Streamline warehouse or pharmacy stock-taking by holding a camera over stacked shelves to automatically count and value detected items.
* **Hospital Ward Medication Tracking:** Assist nursing staff in logging and verifying administered medication packages and tracking daily treatment costs.
* **Elderly Home Care & Smart Pillbox Management:** Help caregivers keep digital ledgers of home-stored medicines and calculate replenishment expenses automatically.

## Installation

Set up a Python environment using a virtual environment, Conda, or Google Colab.

Install the required packages:

```bash
pip install ultralytics easyocr opencv-python matplotlib numpy

```

## Usage

1. Place your trained model weights (`medicine.pt`) and target video (`me3.mp4`) in your workspace directory.
2. Run the video processing pipeline script:

```python
input_vid  = 'me3.mp4'
output_vid = 'm4.mp4'
process_video(input_vid, output_vid)

```

## Model and Data

* Provide YOLOv8 weights trained on custom medicine packaging datasets.
* Update file directory paths within the script according to your local environment configuration.

## Contributing

Pull requests, feature expansions (such as expanded database integrations or UI themes), and bug reports are welcome.

## Credits

* **Detection:** Ultralytics YOLOv8
* **OCR:** EasyOCR
* **Video Processing & UI Rendering:** OpenCV & NumPy
