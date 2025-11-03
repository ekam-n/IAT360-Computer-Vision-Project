# Posture Coach — Webcam Posture Classifier
## Overview

Posture Coach is a lightweight computer-vision project that classifies laptop-style webcam images into three posture states: looks good, sit up straight, and straighten head. The goal is practical quality-of-life feedback for students and desk workers: short, fast fine-tunes on a small YOLO classification backbone; real-time inference from a straight-on, upper-body view; and simple alerts that encourage healthier habits. We optimized for common study setups—indoor lighting, typical laptop camera angles, and everyday clothing—while keeping the model small enough to run smoothly on consumer hardware.

## Dataset

Base dataset (train/val only): Roboflow Posture Correction v4 — https://universe.roboflow.com/posturecorrection/posture_correction_v4

Used only the train and validation splits for training and validation.
License: CC BY 4.0 — provide attribution, link to the license, and indicate if changes were made.

Test set (ours): We collected a laptop-POV test split to better match the intended use. Only this test split is included in the repo.


## Training and evaluation summary

We fine-tuned for 5 epochs with AdamW, cosine learning-rate decay, and a brief warmup to stabilize optimization and limit overfitting to noisy labels. Validation used the Roboflow val split; testing used our laptop-POV test split. We report Top-1 accuracy plus per-class Precision/Recall/F1, along with macro and weighted averages.

## Results highlights

Best model: train22

Validation results: val53

Test results (our data): val54

Runs train21/train22 outperform the baseline train5, especially on our real-world laptop-style test split.

## What’s included

Our test split (only our data).

Selected runs: baseline (train5) and improved models (train21, train22), with their relevant validation and test result folders (val53, val54).

## Notes and limitations

The base dataset includes frames extracted from video; transitional frames can introduce label noise.

Best performance occurs with straight-on, upper-body framing in indoor conditions; bulky clothing or occlusions can hide head-neck cues.

The label set is intentionally simple; finer-grained feedback would require cleaner labels and broader data.

## Acknowledgments

Roboflow Posture Correction v4 (CC BY 4.0) for training/validation data.

Ultralytics YOLO for training and evaluation tooling.

The Roboflow dataset remains under CC BY 4.0; follow attribution requirements when reusing it.
