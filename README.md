# CAPTCHA OCR Decoder

## Overview
A simple web app for uploading a CAPTCHA image and decoding its text using Python's pytesseract (Tesseract OCR). It includes light preprocessing to improve recognition and displays both the original and preprocessed images alongside the detected text.

## Setup
- Requirements:
  - Python 3.8+
  - Tesseract OCR engine installed on your system
  - Python packages: Flask, Pillow, pytesseract

- Install Tesseract:
  - macOS (Homebrew): brew install tesseract
  - Ubuntu/Debian: sudo apt-get update && sudo apt-get install -y tesseract-ocr
  - Windows: Download installer from https://github.com/tesseract-ocr/tesseract and add tesseract.exe to PATH (or set TESSERACT_CMD env var)

- Install Python dependencies:
  - pip install flask pillow pytesseract

- Optional: If Tesseract is not on PATH, set the environment variable:
  - macOS/Linux: export TESSERACT_CMD=/usr/local/bin/tesseract
  - Windows (PowerShell): setx TESSERACT_CMD "C:\Program Files\Tesseract-OCR\tesseract.exe"

## Usage
1. Run the app:
   - python index.html
   - By default it starts at http://localhost:8000

2. In your browser:
   - Open http://localhost:8000
   - Upload a CAPTCHA image (PNG/JPG/etc.)
   - Click "Decode" to see:
     - Original image preview
     - Preprocessed image (grayscale + threshold)
     - Extracted text

Tip: Higher contrast and cleaner inputs yield better OCR. You can tweak the threshold value in preprocess_for_captcha if needed.

## Improvements from previous version (Round 2)
- Added preprocessing: grayscale, median denoise, and binary threshold to improve OCR accuracy on noisy CAPTCHAs.
- Restricted Tesseract to single-line mode with an alphanumeric whitelist for better precision on typical CAPTCHAs.
- Inline previews: show both original and preprocessed images for transparency and easier debugging.
- Robustness: basic file type validation, clearer error messages, and optional TESSERACT_CMD configuration for portability.