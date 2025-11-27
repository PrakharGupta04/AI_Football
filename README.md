# Football Analysis Project

## Introduction
The goal of this project is to detect and track players, referees, and footballs in a video using YOLO, one of the best AI object detection models available. We will also train the model to improve its performance. Additionally, we will assign players to teams based on the colors of their t-shirts using Kmeans for pixel segmentation and clustering. With this information, we can measure a team's ball acquisition percentage in a match. We will also use optical flow to measure camera movement between frames, enabling us to accurately measure a player's movement. Furthermore, we will implement perspective transformation to represent the scene's depth and perspective, allowing us to measure a player's movement in meters rather than pixels. Finally, we will calculate a player's speed and the distance covered. This project covers various concepts and addresses real-world problems, making it suitable for both beginners and experienced machine learning engineers.

![Screenshot](output_videos/screenshot.png)

## Modules Used
The following modules are used in this project:
- YOLO: AI object detection model
- Kmeans: Pixel segmentation and clustering to detect t-shirt color
- Optical Flow: Measure camera movement
- Perspective Transformation: Represent scene depth and perspective
- Speed and distance calculation per player

## Trained Models
- [Trained Yolo v5](https://drive.google.com/file/d/1DC2kCygbBWUKheQ_9cFziCsYVSRw6axK/view?usp=sharing)

## Sample video
-  [Sample input video](https://drive.google.com/file/d/1t6agoqggZKx6thamUuPAIdN_1zR9v9S_/view?usp=sharing)

## Requirements
To run this project, you need to have the following requirements installed:
- Python 3.x
- ultralytics
- supervision
- OpenCV
- NumPy
- Matplotlib
- Pandas

## Quick Start

1. Create and activate a virtual environment (recommended):

   Windows PowerShell:
   ```powershell
   cd C:\Users\praba\OneDrive\Desktop\AI_Football\football_analysis
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

2. Install dependencies:
   ```powershell
   pip install -r requirements.txt
   ```

3. Add required assets:
   - Input video: place a football match video at `input_videos/08fd33_4.mp4`.
     - You can use the provided sample: see link in Sample video above.
   - Model weights (optional for stubbed run): place YOLO weights at `models/best.pt` if you want to run real detections. The default `main.py` is configured to use pre-generated stubs, so weights are not required to produce an example output.

4. Run the project:
   ```powershell
   python main.py
   ```

5. Output:
   - The annotated video will be saved to `output_videos/output_video.avi`.

## Notes

- The tracker is configured to use precomputed stubs by default (`stubs/track_stubs.pkl` and `stubs/camera_movement_stub.pkl`). This allows running without downloading large model files.
- To run full detection instead of stubs, ensure `models/best.pt` exists and change `read_from_stub=False` in `main.py` where `Tracker.get_object_tracks(...)` is called, and similarly disable stub usage for the camera movement estimator.

## Troubleshooting

- If you see an error about a missing input video, ensure you have added a video at `input_videos/08fd33_4.mp4`.
- If you encounter import errors, make sure you activated the virtual environment and installed requirements.
- For GPU acceleration, install the CUDA-enabled PyTorch per the official guide and reinstall `torch`, `torchvision`, and `torchaudio` accordingly.

## Debug & Tuning Toolkit

- **Polished pipeline command** (from `football_analysis/`):
  ```powershell
  python main.py --video input_videos/08fd33_4_small.mp4 --resize_width 720
  ```
- **Key tuning knobs** (pass as CLI args to `main.py`):
  - `--pass_dist_thresh`, `--pass_speed_thresh`, `--shot_speed_thresh`
  - `--sender_lookup_window`, `--receiver_lookup_window`
  - `--min_receiver_proximity`, `--min_ball_travel_for_pass`
  - `--trail_length`, `--meters_per_pixel`, `--motion_smooth_window`
- **Debug artifacts**:
  - `debug_first_annotated_frame.jpg` — inspect badge placement, colors, overlays.
  - `output_videos/events.csv` (and automatic `events_alt.csv` fallback) — check the first 20 rows with:
    ```powershell
    python debug_inspect.py --events output_videos/events.csv
    ```
- **Video IO smoke test**:
  ```powershell
  python test_read_video.py --video input_videos/08fd33_4_small.mp4
  ```
  Saves `output_videos/test_read_video_first_frame.jpg` so you can confirm decoding without running the full pipeline.