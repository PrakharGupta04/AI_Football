 **AI Football Analysis System**

Advanced computer vision pipeline for football match analysis using YOLO, ByteTrack, color clustering, optical flow, and deep analytics.

** Overview
**
This project performs end-to-end football match analysis, including:

 Player, referee & ball detection using YOLO

 Multi-object tracking using ByteTrack

 Automatic team assignment using K-Means color clustering

 Ball possession tracking

 Pass, shot & interception event detection

 Comprehensive player and team statistics

 Perspective transformation for real-world measurements

 Speed & distance estimation

 Advanced match visualizations (badges, trails, arrows, overlays)

 Zone analysis (ball presence & player density)

 Passing network analysis (graph, centrality, heatmaps)

 AI Action Suggestions (intelligent pass/dribble/shot recommendations)

This system integrates Computer Vision, Machine Learning, Data Analytics, and Sports Intelligence into one unified workflow.

**Project Architecture**
football_analysis/
│
├── ai_module/                  # Action suggestion system
├── analysis/                   # CSV → statistics → visualizations
├── camera_movement_estimator/  # Optical flow–based camera motion
├── team_assigner/              # K-Means color clustering
├── trackers/                   # YOLO + ByteTrack tracking pipeline
├── view_transformer/           # Perspective transformation
├── utils/                      # Video utils, bbox utils
├── visualization.py            # Advanced overlays, pass arrows, trails
├── main.py                     # Main pipeline (run this)
└── stubs/                      # Pre-generated tracking/camera stubs

**⭐ Key Features**
**1️ Player & Ball Detection**

Uses YOLOv8 (ultralytics)

Converts detections to supervision.Detections

Tracks objects across frames using ByteTrack

**2️ Team Assignment**

K-Means color clustering

Multi-frame sampling for robustness

Produces team ID + team color for each player

**3️ Camera Movement Estimation**

Sparse optical flow
Stabilizes positions for accurate speed estimation

**4️ Perspective Transformation**

Maps pixel positions to real-world coordinates.

**5️ Speed & Distance Estimation**

Uses transformed points to compute:
m/s
km/h
distance traveled

**6️ Ball Possession Tracking**

Assigns ball to nearest player per frame
Computes:
per-frame possession
total % possession per team

**7️ Event Detection System**

Detects:
successful passes
interceptions
shots
pass trajectories
Outputs → events.csv

**8️ AI Action Suggestions**

For each frame, system evaluates:
pass options
shot possibilities
dribble opportunities
Scores actions using heuristic models
receiver open space
passing lane clearance
positional advantage
distance / risk evaluation

**9️ Advanced Visual Overlays**
The visualization module renders:
ID badges with team colors
speed & distance text
trails showing movement
pass arrows
shot markers
camera movement overlay
team legends

 **10.Analytics & Reports**
1.CSV Outputs
2.Player stats
3.Team stats
3.Event logs
4.Pass success & distance reports
5.Visual Charts
6.Pass completion chart
7.Team comparison
8.Pass distance histogram + boxplot
9.Time-based pass activity
10.Zone Analysis
11.Ball presence heatmap
12.Player density heatmap
13.Passing Network
14.Directed weighted graph
15.Node centrality metrics
16.Top passers
17.Adjacency matrices
18.Interactive HTML graph (optional)

** Installation**
1. Create virtual environment
   
python -m venv .venv
.\.venv\Scripts\Activate.ps1

2. Install dependencies
   pip install -r requirements.txt

**Running the Project**
**Run the full pipeline**
python main.py --video input_videos/match.mp4 --resize_width 720

**Generate full analysis suite**
python analysis/run_all_analysis.py

**Output Structure**
outputs/
├── videos/                        # Final annotated video
├── analysis/                      # CSV + JSON stats
├── visualizations/                # Graphs & plots
├── zone_analysis/                 # Heatmaps
├── pass_network_outputs/          # Network graphs + JSON
└── debug/                         # First annotated frame


 **Debug & Tools**
1. View first annotated frame
python debug_inspect.py --events output_videos/events.csv

2. Test video decoding
python test_read_video.py --video input_videos/sample.mp4

3. Visual regression test
python visual_test_small.py


** References**

YOLOv8 — Ultralytics

ByteTrack — Multi-object tracking

Optic Flow — Lucas-Kanade

OpenCV Homography

**📜 License**

This project is released under the MIT License.

**🙌 Author**

**Prakhar Gupta
AI/ML Engineering • Computer Vision • Sports Analytics**
