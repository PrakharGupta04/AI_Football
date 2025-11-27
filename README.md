⚽ AI Football Analysis System

A complete computer vision + analytics pipeline for football match analysis, featuring YOLO-based detection, ByteTrack tracking, team identification, pass detection, match statistics, action suggestions, visual overlays, zone heatmaps, and passing network graphs.

This system brings together Computer Vision, Machine Learning, Optical Flow, Color Clustering, Data Analytics, and Sports Intelligence into one unified platform.

📌 Overview

This project performs end-to-end automated football match analysis:

⚽ Player, referee & ball detection using YOLOv8

➿ Multi-object tracking using ByteTrack

🎽 Team assignment using K-Means color clustering

🟢 Ball possession tracking

🎯 Event detection (passes, shots, interceptions)

📈 Player & team performance analytics

🌍 Perspective transformation (pixel → real-world coordinates)

🏃‍♂️ Speed & distance estimation per player

🎥 Advanced visual overlays (IDs, trails, arrows, speed, distance)

🗺 Zone analysis (ball presence & player density heatmaps)

🔗 Passing network analysis (centrality, adjacency, graph visuals)

🧠 AI action suggestions (best pass/dribble/shot options)

This system is modular, optimized, and designed to run on any football broadcast video.

🏗️ Project Architecture
football_analysis/
│
├── ai_module/                 # Action suggestion engine
├── analysis/                  # CSV → statistics → charts
├── camera_movement_estimator/ # Optical-flow-based camera motion correction
├── team_assigner/             # K-Means color clustering for team detection
├── trackers/                  # YOLOv8 + ByteTrack tracking pipeline
├── view_transformer/          # Perspective transform (pixel → meters)
├── utils/                     # Video I/O, bbox utils
├── visualization.py           # Overlays (IDs, trails, passes, etc.)
├── main.py                    # Main pipeline (run this)
└── stubs/                     # Pre-generated tracking/camera stubs (no model needed)

⭐ Key Features
🔹 1. Player, Referee & Ball Detection

YOLOv8s via ultralytics

Detection → supervision.Detections

Clean bounding box extraction

🔹 2. Multi-Object Tracking

ByteTrack for persistent player IDs

Smooth tracking even with rapid motion

Automatic handling of lost & reappearing players

🔹 3. Team Assignment (K-Means)

Multi-frame sampling of jersey pixels

Clustering into Team 1 & Team 2

Automatic team color extraction

Extremely robust across lighting & camera shifts

🔹 4. Camera Movement Estimation

Lucas–Kanade optical flow

Frame-to-frame camera shift vector

Ensures accurate player speed / distance measurement

🔹 5. Perspective Transformation

Homography-based top-down projection

Converts pixel coordinates → meters

Enables accurate speed (km/h) & distance (m) calculations

🔹 6. Speed & Distance Estimation

Per-frame movement tracking

Computes:

Speed (m/s & km/h)

Distance traveled (meters)

Smooth trajectory paths

🔹 7. Ball Possession Detection

Ball → nearest player assignment

Computes:

Frame-by-frame possession

Team possession %

Possession timeline overlay on video

🔹 8. Event Detection (AI-based)

Detects:

Passes

Interceptions

Shots

Pass trajectory distances

Pass speeds

Outputs to:
📄 events.csv

🔹 9. AI Action Suggestions

For each frame, evaluates:

Best pass option

Best dribble direction

Best shot opportunity

Considers:

Open passing lanes

Opponent proximity

Field advantage

Risk vs reward

Distance & angle

Receiver availability

🔹 10. Advanced Visual Overlays

Rendered on video:

Team-colored player ID badges

Speed & distance values

Movement trails

Pass arrows (successful & intercepted)

Shot markers

Camera movement overlay

Team legend

🔹 11. Analytics & Reporting
📊 CSV Outputs

player_statistics.csv

events.csv

comprehensive_stats_report.json

📈 Visual Charts

Pass completion by player

Team comparison

Pass distance distribution

Passes over time

🗺 Zone Analysis

Ball presence heatmap

Player density heatmap

🔗 Passing Network

Adjacency matrices

Network graphs

Centrality analysis (degree, betweenness, pagerank)

Top passers

Interactive HTML visualizations

⚙️ Installation
1️⃣ Create virtual environment
python -m venv .venv
.\.venv\Scripts\Activate.ps1

2️⃣ Install dependencies
pip install -r requirements.txt

▶️ Running the Project
🟢 Run full pipeline
python main.py --video input_videos/match.mp4 --resize_width 720

🟡 Generate all analytics
python analysis/run_all_analysis.py

📁 Output Structure
outputs/
├── videos/                  # Final annotated video
├── analysis/                # CSV + JSON stats
├── visualizations/          # Graphs & plots
├── zone_analysis/           # Heatmaps
├── pass_network_outputs/    # Network graphs + adj matrices
└── debug/                   # First annotated frame

🧪 Debug Tools
Check annotated frame
python debug_inspect.py --events output_videos/events.csv

Test video decoding
python test_read_video.py --video input_videos/sample.mp4

Test visualization rendering
python visual_test_small.py

📚 References

YOLOv8 – Ultralytics

ByteTrack – Multi-object tracking

OpenCV Optical Flow – Lucas–Kanade

OpenCV Homography – Perspective transform

📝 License

This project is licensed under the MIT License.

👤 Author

Prakhar Gupta
AI/ML Engineer
Computer Vision • Deep Learning • Sports Analytics
