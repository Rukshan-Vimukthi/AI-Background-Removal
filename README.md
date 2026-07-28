# AI-Background-Removal
AI deep learning model trained to remove/blur background of images and videos

## Overview
This project started from a personal problem.

I wanted to create professional-looking videos with a blurred background effect similar to modern video conferencing and content creation tools. However, existing online solutions either required expensive subscriptions or had limitations that make them impractical for my workflow

Instead of depending on external platforms, I decided to build my own deep learning-based background segmentation system.

The goal was to create a model capable of accurately separating foreground objects from the background and generate masks that can be used for:

- Background blur
- Background replacement
- Image background removal
- Video background processing

---

# The Problem

Applying background blur to videos requires accurately identifying the foreground object in every frame

Traditional image processing techniques struggle because:

- Background can be complex
- Lighting conditions vary
- Object boundaries require pixel-level accuracy
- Video processing requires consistent masks between frames

Commercial AI solutions solve this problem using trained segmentation models, but they were not accessible for my personal workflow

This motivated me to build a custom deep learning solution

---

# Solution

I developed an encoder-decoder segmentation model that learns to generate foreground mass from images

The model:

- Receives an RGB image frame
- Extracts visual features using an encoder network
- Reconstruct spatial information using a decoder network
- Produces a pixel level foreground mask

The generated mask can them be used to separate the subject from the background

---

# Architecture

![Model Architecture](docs/architecture.png)

The model uses:

- Encoder-decoder architecture
- Residual feature extraction blocks
- Skip connections for preserving spatial details
- Custom loss function to improve boundary accuracy

---

# Applications

## Image Background Removal

The model can generate foreground masks for individual images.

Examples:

(Add before/after images)

## Video background blur

The same model is applied frame-by-frame to videos.

Pipeline:
```
Video Input
    |
Frame Extraction
    |
AI Segmentation Model
    |
Foreground Mask Generation
    |
Background Blur Processing
    |
Final Video Output
```

---

# Training Approach

The model was trained using a custom dataset pipeline with image augmentation techniques including:

- Blur Simulation
- Resolution degradation
- Image transformations

These augmentations help the model handle real-world video conditions

---

# Technologies

- Python
- TensorFlow / Keras
- OpenCV
- NumPy
- Google Colab GPU

---

# Results

The model successfully generates segmentation masks suitable for:

- Portrait background blur
- Image background removal
- Video background processing

(Add demo images/videos here)
![Model Result](demo/before_after_images)

---

# Future Improvements:

- Real-time video inference
- Temporal consistency optimization
- Mobile deployment
- ONNX/TensorRT optimization
