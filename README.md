# AI Obstacle Detection System for the Visually Impaired

A real-time computer vision system designed to help visually impaired users
identify obstacles while navigating their surroundings.

## Overview

The system uses a custom-trained YOLOv8n object detection model to identify
22 types of urban obstacles from a smartphone camera feed.

Detected obstacles are displayed using bounding boxes and announced through
the browser's Web Speech API.

## Architecture

- **YOLOv8n** — object detection model
- **FastAPI** — prediction server
- **Google Colab** — training and inference environment
- **ngrok** — exposes the Colab API
- **HTML / JavaScript** — browser-based camera client
- **Web Speech API** — audio alerts
- **Roboflow** — dataset integration and preprocessing

The system captures a camera frame approximately once per second, sends it
to the FastAPI backend, performs YOLO inference, and returns the detected
obstacles to the browser.

## Model

The model was trained using transfer learning from YOLOv8n pre-trained on
COCO.

- Epochs: 25
- Image size: 640 × 640
- Confidence threshold: 0.40
- Hardware: Google Colab T4 GPU
- Classes: 22

## Results

The reported end-to-end latency during browser testing was approximately
200–300 ms at a 1 FPS scan rate.

The system successfully detected obstacles including potholes, open
manholes, poles, motorcycles, persons, curbs, and road cracks.

## Project Files

- [Jupyter Notebook](AI_Project_VisuallyImpaired.ipynb)
- [Project Report](AI_Obstacle_Detection_Report.pdf)

## Limitations

The current implementation depends on:
- an internet connection
- a Google Colab GPU runtime
- an ngrok tunnel
- a 1 FPS scanning rate

The ngrok URL also changes when the Colab session restarts.

## Future Work

Potential improvements include:
- on-device inference using ONNX or TensorFlow Lite
- increasing the frame rate to 5–10 FPS
- depth estimation for distance-based alerts
- additional model training
- wearable integration
- structured testing with visually impaired users
