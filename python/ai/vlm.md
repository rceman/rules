# 👀 Vision Model (VLM) Rules

## 1. Model Choice

| Model                       | Size | Comment                       |
|-----------------------------|------|-------------------------------|
| xtuner/llava‑llama‑3‑8b     | 8 GB | good text‑UI understanding    |
| moat‑vlm‑base               | 2 GB | very fast, lower quality      |

## 2. Runtime

Use `llama-cpp-python[vision]` (vision patch).  
Batch multiple frames to improve throughput.

## 3. OCR fallback

If the VLM fails to read fine text, fallback to **pytesseract**.

* Pre‑process screenshot: grayscale & threshold.

## 4. Security

Mask sensitive data (password fields) before saving screenshots.
