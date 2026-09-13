<div align="center">

# Medicine Label Detection and Recognition

An automated computer vision pipeline that detects medicine packaging and extracts medicine names from label text. The system uses a custom-trained YOLOv8 model for detection and EasyOCR for text recognition. The pipeline supports single images and videos and produces annotated frames with detected boxes and recognized text.

<p>
  <img src="assets/python.svg" alt="Python" width="48" height="48" />
  <img src="assets/jupyter.svg" alt="Jupyter Notebook" width="48" height="48" />
  <img src="assets/opencv.svg" alt="OpenCV" width="48" height="48" />
  <img src="assets/ultralytics.svg" alt="Ultralytics YOLOv8" width="48" height="48" />
  <img src="assets/pytorch.svg" alt="PyTorch" width="48" height="48" />
</p>

</div>

<div align="center">

## Key features

- Targeted detection using a custom YOLOv8 nano model to locate medicine packaging in complex scenes.
- Focused OCR extraction by cropping detected regions before passing them to EasyOCR to reduce background noise.
- Support for images and video: process single frames or entire videos frame by frame.
- Clear visual output: annotated bounding boxes with semi-transparent fill and a dark text card for high contrast.

## Pipeline overview

1. Frame input: load an image or a video frame and convert color spaces as required for detection and OCR.
2. Object detection: YOLOv8 returns bounding box coordinates for detected medicine packaging.
3. Cropping: extract the bounding box region from the original frame.
4. Text recognition: pass the cropped region to EasyOCR and obtain detected text.
5. Rendering: draw the bounding box, create a dark text card, and render the OCR result onto the original frame.

</div>

## Installation

Set up a Python environment. We recommend using a fresh virtual environment, Conda, or Google Colab.

Install required packages:

```bash
pip install ultralytics easyocr opencv-python matplotlib numpy
```

## Usage

- Open and run the main notebook included in this repository.
- For images: set the path to an input image and model weights, then run the image inference cell.
- For video: set the path to an input video and model weights, then run the video processing cell to generate an annotated output video.

Adjust file paths for model weights and input data in the notebook before running.

## Model and data

- Provide YOLOv8 weights trained on labeled images of medicine packaging. Update the notebook to point to your weights file.
- Place example images or videos in a folder and update notebook paths for inference.

## Adding icons

Place the following files in an `assets/` directory at the repository root:

- assets/python.svg
- assets/jupyter.svg
- assets/opencv.svg
- assets/ultralytics.svg
- assets/pytorch.svg

SVG files are included in this commit. If you prefer different logos, replace the files in the assets/ directory.

## Contributing

If you add model weights, sample data, or example notebooks, please include short usage notes and attribution for data sources.

## Credits

- Detection: Ultralytics YOLOv8
- OCR: EasyOCR
- Image processing and rendering: OpenCV

## License

Add or update a LICENSE file to specify the desired license for this repository. If you prefer a permissive license, consider adding an MIT License file.
