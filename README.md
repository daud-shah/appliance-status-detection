# 🏠 Appliance Status Detection System

![Python](https://img.shields.io/badge/Python-3.11+-blue)
![YOLO](https://img.shields.io/badge/YOLO-Ultralytics-red)
![OpenCV](https://img.shields.io/badge/OpenCV-4.5+-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)

A computer vision system that detects and classifies the operational status of home appliances (AC, Fan, Light) using YOLOv8 object detection.

## 🌟 Features

- **Real-time appliance detection** using YOLOv8
- **Status classification** (On/Off states):
  - AC-Off/On
  - Fan-Off/On
  - Light-Off/On
- **Video processing**:
  - Frame-by-frame analysis
  - Annotated output video generation
- **Performance optimized**:
  - GPU acceleration support
  - Configurable confidence thresholds

## 🛠️ Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/appliance-status-detection.git
   cd appliance-status-detection
   ```

2. **Install dependencies**:
   ```bash
   pip install ultralytics<=8.3.40 opencv-python supervision roboflow
   ```

3. **Download model weights**:
   - Place your trained YOLO model (`best.pt`) in the project directory

## 🚀 Usage

### Process a video file:
```bash
python process_video.py --input input.mp4 --output output.mp4
```

### Optional arguments:
- `--model`: Path to custom weights (default: `best.pt`)
- `--conf`: Confidence threshold (default: 0.25)
- `--iou`: IoU threshold (default: 0.25)
- `--device`: Device ID (0 for GPU, 'cpu' for CPU)

### Example code:
```python
from ultralytics import YOLO

# Load model
model = YOLO("best.pt")

# Process single image
results = model("room.jpg", conf=0.25)
results[0].show()  # Display results
```

## 📂 Project Structure

```
appliance-status-detection/
├── process_video.py      # Main processing script
├── best.pt              # YOLOv8 model weights
├── sample_videos/       # Example input videos
├── output/             # Processed results
└── README.md           # This documentation
```

## 🔍 Detection Classes

| Class ID | Class Name | Sample Color |
|----------|------------|--------------|
| 0        | AC-Off     | Red          |
| 1        | AC-On      | Green        |
| 2        | Fan-Off    | Blue         |
| 3        | Fan-On     | Cyan         |
| 4        | Light-Off  | Yellow       |
| 5        | Light-On   | White        |

## ⚙️ Technical Details

**Processing Pipeline**:
1. Frame extraction from input video
2. YOLOv8 inference on each frame
3. Status classification for each appliance
4. Bounding box annotation with:
   - Class labels
   - Confidence scores
   - Color-coded status indicators
5. Output video compilation

**Performance**:
- ~9ms per frame on NVIDIA Tesla T4 GPU
- Real-time capable at 30+ FPS

## 📈 Future Improvements

- [ ] Real-time webcam integration
- [ ] Energy consumption estimation
- [ ] Multi-appliance tracking
- [ ] Web interface/dashboard
- [ ] Alert system for left-on appliances

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-detection`)
3. Commit your changes (`git commit -m 'Add new appliance detection'`)
4. Push to the branch (`git push origin feature/new-detection`)
5. Open a Pull Request

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---
