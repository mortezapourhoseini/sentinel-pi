Real-Time Person Detection for Raspberry Pi

Overview
Ultra-low latency person detection system optimized for Raspberry Pi 3B+. Captures video from camera, runs inference with YOLO11, and streams results via web interface with minimal delay.

Hardware
- Raspberry Pi 3B+
- Raspberry Pi Camera Module v1.3

Software Stack
- YOLO11 (Object Detection Model)
- TensorFlow Lite (yolo11n_float32.tflite)
- Python 3
- Flask (Web Framework)
- OpenCV (Image Processing)
- PiCamera (Camera Control)

Features
- Real-time person detection at 30 FPS
- Hardware-efficient inference with frame skipping
- Aggressive frame dropping to minimize buffering latency
- Web-based live streaming interface
- Performance statistics endpoint

Installation

1. Clone or setup the project directory
2. Install dependencies
   pip3 install flask tflite-runtime opencv-python picamera numpy

3. Place model file
   mkdir -p models
   cp yolo11n_float32.tflite models/

4. Run the application
   python3 person_detection.py

5. Access web interface
   Open browser and navigate to http://<raspberry-pi-ip>:5000

Configuration
Edit these values in person_detection.py to tune performance:
- CAMERA_WIDTH / CAMERA_HEIGHT: Capture resolution
- INFERENCE_SKIP_FRAMES: Run inference every N frames
- JPEG_QUALITY: Compression level (lower = faster)
- CAMERA_FRAMERATE: Frames per second

Performance Notes
Designed for minimal latency on resource-constrained hardware. Uses non-blocking queue operations, aggressive frame dropping, and frame skipping to achieve <100ms end-to-end latency.

Files
- person_detection.py: Main application
- models/yolo11n_float32.tflite: YOLO11 nano model (TensorFlow Lite format)
- models/coco_labels_person.txt: COCO class labels
