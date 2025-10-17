# CAPTCHA OCR Decoder

## Overview
This is a simple web app that lets you upload a CAPTCHA image and automatically decodes its text using Python OCR (pytesseract). The server preprocesses the image (denoising, contrast enhancement, binarization) to improve recognition, then runs Tesseract via pytesseract and shows the result on the page.

Key features:
- Image upload form (browser-based UI)
- Python backend with Flask
- OCR via pytesseract (Tesseract engine)
- Displays decoded text and previews of original and preprocessed images

## Setup

1. Install system Tesseract OCR:
   - macOS (Homebrew):
     - brew install tesseract
   - Ubuntu/Debian:
     - sudo apt-get update
     - sudo apt-get install -y tesseract-ocr
   - Windows:
     - Download and install from https://github.com/tesseract-ocr/tesseract
     - After installing, ensure tesseract.exe is on your PATH. If not, you can set:
       - In Python: pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"

2. Create and activate a Python environment (optional but recommended):
   - python -m venv .venv
   - On macOS/Linux: source .venv/bin/activate
   - On Windows: .venv\Scripts\activate

3. Install Python dependencies:
   - pip install Flask pillow pytesseract

## Usage

1. Run the app:
   - python index.html

   The server starts on http://localhost:5000 (or the PORT defined in your environment).

2. Open the app in your browser:
   - Navigate to http://localhost:5000

3. Upload a CAPTCHA image:
   - Click “Choose File”, select your image, then “Decode CAPTCHA”.
   - The page will display:
     - Decoded text result
     - Original image preview
     - Preprocessed image preview (what is fed to OCR)

Tips:
- Single-line, high-contrast CAPTCHAs work best.
- If no text is detected, try adjusting your image quality or contrast.
- On Windows, if you see “TesseractNotFoundError,” set the tesseract executable path as mentioned above.