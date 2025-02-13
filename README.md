# Stereo Depth Estimation

## Overview
This project implements **stereo vision-based depth estimation** using OpenCV and NumPy. It performs feature matching, fundamental and essential matrix computation, stereo rectification, and disparity-to-depth conversion.

## Features
- **Feature Matching:** ORB (Oriented FAST and Rotated BRIEF) + Brute-Force Matcher
- **Fundamental & Essential Matrix Computation** for epipolar geometry
- **Camera Pose Estimation** (Rotation & Translation extraction)
- **Stereo Rectification** (Aligning images for proper disparity computation)
- **Disparity & Depth Mapping** using Stereo Block Matching

## Installation
To run this project in Google Colab, you need:
1. **Google Drive access** to store dataset images.
2. Install dependencies (most are pre-installed in Colab):
    ```python
    !pip install opencv-python numpy matplotlib
    ```

## Dataset
The project uses stereo image pairs stored in Google Drive. Modify the path accordingly.

## Running the Code
1. **Mount Google Drive:**
    ```python
    from google.colab import drive
    drive.mount('/content/drive/', force_remount=True)
    ```
2. **Run the pipeline for a dataset:**
    ```python
    storage_room()
    ```
   Other datasets:
   - `class_room()`
   - `trap_room()`

## Explanation of Key Steps
### 1. Feature Matching
Detects and matches keypoints between stereo images using ORB and BFMatcher.

### 2. Fundamental & Essential Matrices
- The **fundamental matrix (F)** defines epipolar geometry.
- The **essential matrix (E)** is derived from F using camera calibration parameters.
- Camera pose (rotation R & translation T) is extracted from E.

### 3. Stereo Rectification
Aligns stereo images so epipolar lines are horizontal, improving disparity estimation.

### 4. Depth Estimation
Converts disparity to depth using:

   \[
   Depth = rac{Baseline 	imes Focal Length}{Disparity}
   \]

## Results
- **Rectified Stereo Images**: Properly aligned images
- **Disparity Map**: Shows pixel differences between images
- **Depth Map**: Represents 3D depth information

## Applications
- **Autonomous Vehicles**: Obstacle detection & depth sensing
- **Robotics**: 3D environment understanding
- **Augmented Reality**: Depth-based interactions

