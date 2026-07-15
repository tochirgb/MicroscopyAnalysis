# MicroscopyAnalysis
CNN + YOLOv8 pipeline for detecting and classifying steel surface defects (crazing, inclusions, patches, pitted surface, rolled-in scale, scratches) from SEM micrographs. Includes a ResNet-18 classifier (~98% accuracy), YOLOv8 defect localization, Grad-CAM interpretability, and a deployed Gradio demo — built as a non-destructive testing tool bridging metallurgy and computer vision.

# Steel Surface Defect Detection

A computer vision pipeline for automated defect detection in steel micrographs, built for non-destructive testing (NDT) applications in materials failure analysis.

## Overview

This project classifies and localizes six types of surface defects — crazing, inclusions, patches, pitted surface, rolled-in scale, and scratches — using the NEU-DET dataset. It combines a CNN classifier with object detection and interpretability tools to move beyond a single accuracy number toward a system that explains *why* it flags what it flags.

## Why this matters

Manual visual inspection of steel surfaces is slow, inconsistent, and misses sub-visible defects. Each defect class here traces back to a specific point in the rolling/manufacturing process — this project treats that physical context as a first-class part of the model, not an afterthought.

## Pipeline

- **Baseline CNN** — from-scratch classifier (~90% accuracy), used as a comparison point
- **ResNet-18 (transfer learning)** — ~98% classification accuracy across 6 classes
- **YOLOv8** — defect detection with bounding boxes, mAP@0.5 ~0.77
- **Grad-CAM** — visualizes model attention to verify it's keying on the actual defect region, not background artifacts
- **Gradio demo** — live inference: upload a micrograph, get class probabilities + detection boxes + heatmap

## Dataset

[NEU-DET](https://www.kaggle.com/datasets/kaustubhdikshit/neu-surface-defect-database) — 1,800 labeled SEM-style images of hot-rolled steel strip.

## Results

| Model | Accuracy | mAP@0.5 |
|---|---|---|
| Baseline CNN | ~90% | — |
| ResNet-18 | ~98% | — |
| YOLOv8n | — | ~0.77 |

## Demo

[Live Hugging Face Space link here](https://f76e0f5fc0a291b47e.gradio.live/)

## Tech stack

PyTorch, torchvision, Ultralytics YOLOv8, Albumentations, Grad-CAM, Gradio
