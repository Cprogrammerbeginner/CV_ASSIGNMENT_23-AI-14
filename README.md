# Pose-Based Activity Recognition using MediaPipe and OpenCV

## Overview

This project implements a real-time human activity recognition system using **MediaPipe Pose Landmarker** and **OpenCV**. The system detects human body landmarks from video frames, computes joint angles, and classifies activities into:

* Running
* Walking
* Jumping

The project uses a rule-based classification approach based on biomechanical body movements and joint angle analysis.

## Features

* Real-time pose detection using MediaPipe
* Extraction of 33 body landmarks per frame
* Joint angle computation using vector mathematics
* Temporal smoothing for stable predictions
* Rule-based activity classification
* Annotated output video generation
* Joint angle visualization graphs
* Accuracy evaluation of activity predictions

## Technologies Used

* Python
* OpenCV
* MediaPipe
* NumPy
* Matplotlib
* Google Colab

## Dataset / Input

The system works on merged activity videos containing:

* Running sequences
* Walking sequences
* Jumping sequences

The input video is processed frame-by-frame for pose estimation and activity classification.

## Videos

/content/joint_angles.png
/content/jumping_man_video.mp4
/content/running_man_video.mp4
/content/merged_video.mp4


## Pipeline Workflow

1. Video Loading and Processing
2. Pose Detection using MediaPipe
3. Landmark Extraction
4. Temporal Keypoint Smoothing
5. Joint Angle Computation
6. Rule-Based Activity Classification
7. Video Annotation
8. Accuracy Evaluation
9. Visualization of Results

## Body Landmarks Used

The following body landmarks are used for angle computation:

| Landmark       | Index |
| -------------- | ----- |
| Left Shoulder  | 11    |
| Right Shoulder | 12    |
| Left Elbow     | 13    |
| Right Elbow    | 14    |
| Left Wrist     | 15    |
| Right Wrist    | 16    |
| Left Hip       | 23    |
| Right Hip      | 24    |
| Left Knee      | 25    |
| Right Knee     | 26    |
| Left Ankle     | 27    |
| Right Ankle    | 28    |

## Angle Computation

Joint angles are computed using the vector-based angle formula:

[
\theta = \cos^{-1}\left(\frac{BA \cdot BC}{|BA| \cdot |BC|}\right)
]

The following angles are calculated:

* Left Knee Angle
* Right Knee Angle
* Left Elbow Angle
* Hip Angle

## Activity Classification Logic

The classification is based on threshold rules using:

* Knee average angle
* Knee angle difference
* Hip angle

### Classification Rules

| Condition                           | Activity |
| ----------------------------------- | -------- |
| Deep knee + hip bend                | Jumping  |
| High knee asymmetry                 | Running  |
| Moderate movement + upright posture | Walking  |

## Temporal Smoothing

A sliding window average of 5 frames is applied to reduce noise and jitter in landmark detection.

## Output Files

The project generates:

* `output_annotated.mp4` → Annotated activity recognition video
* `joint_angles.png` → Joint angle visualization graph
* `classification_results.png` → Classification performance results

## Results

| Metric           | Performance |
| ---------------- | ----------- |
| Overall Accuracy | 85% – 92%   |
| Running Accuracy | 88% – 95%   |
| Walking Accuracy | 75% – 88%   |
| Jumping Accuracy | 80% – 90%   |

## Observations

* Temporal smoothing significantly improves prediction stability.
* Knee asymmetry is highly effective for running detection.
* Walking and running transitions are the most challenging cases.
* Jumping is reliably detected during takeoff and landing phases.
* Occlusion and motion blur can affect landmark detection accuracy.

## How to Run

### 1. Clone the Repository

```bash
git clone <your-repository-link>
cd <repository-folder>
```

### 2. Install Dependencies

```bash
pip install opencv-python mediapipe numpy matplotlib
```

### 3. Run the Notebook

Open the Jupyter Notebook or Google Colab file and execute all cells.

## Project Structure

```bash
├── CV_ASSIGNMENT.ipynb
├── output_annotated.mp4
├── joint_angles.png
├── classification_results.png
├── README.md
```

## Applications

* Human Activity Recognition
* Sports Analytics
* Fitness Tracking
* Surveillance Systems
* Smart Healthcare Monitoring

## Future Improvements

* Deep Learning-based activity classification
* Multi-person activity recognition
* Real-time webcam integration
* Additional activity classes
* Higher accuracy with advanced temporal models

## Author

**Asad Ahmed**
Roll No: 23-AI-14
Subject: Computer Vision

## License

This project is developed for academic and educational purposes.
