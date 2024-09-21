# Vehicle Counting using YOLOv8 and ByteTrack

This repository contains the final project for the **Image Analysis and Computer Vision Course (A.Y. 22/23) at Politecnico di Milano**. The project focuses on detecting and tracking vehicles using **YOLOv8** and **ByteTrack** to achieve accurate vehicle counting in video streams.

## Table of Contents

- [Introduction](#introduction)
- [Technologies](#technologies)
- [Approach](#approach)
  - [YOLOv8 Object Detection](#yolov8-object-detection)
  - [ByteTrack Multi-Object Tracking](#bytetrack-multi-object-tracking)
  - [Other Techniques](#other-techniques)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Conclusion](#conclusion)


## Introduction

This project aims to detect, track, and count vehicles in video streams using modern object detection and tracking techniques. Vehicle counting is challenging due to factors such as overlapping objects, occlusions, and varying lighting conditions. To address these issues, the project leverages **YOLOv8** for object detection and **ByteTrack** for robust multi-object tracking.

## Technologies

- **YOLOv8**: A powerful object detection model that identifies vehicles in each video frame.
- **ByteTrack**: A multi-object tracking algorithm that ensures accurate vehicle tracking across frames.
- **Kalman Filter**: Used in ByteTrack for tracking vehicles even when they are occluded or momentarily lost.
- **Adaptive Histogram Equalization (AHE)**: Used to enhance frame contrast, improving detection accuracy in challenging conditions.

## Approach

### YOLOv8 Object Detection

We use **YOLOv8** to detect vehicles in each frame. YOLOv8 is known for its high accuracy and real-time performance, making it ideal for detecting vehicles in video streams. It identifies and classifies vehicles while predicting their bounding boxes.

### ByteTrack Multi-Object Tracking

For tracking, **ByteTrack** assigns unique IDs to detected vehicles, allowing for consistent tracking across multiple frames. This ensures that vehicles are only counted once, even if they temporarily leave the frame or are partially occluded. ByteTrack is particularly robust in low-confidence detection scenarios.

### Other Techniques

- **Adaptive Histogram Equalization (AHE)**: This technique improves image contrast, making vehicle detection easier in scenes with low contrast or poor lighting.
- **SORT and DeepSORT**: Initially explored for tracking, but ByteTrack outperformed them in robustness and occlusion handling.

## Installation

To set up the project locally, follow these steps:

1. **Clone the repository**:

    ```bash
    git clone https://github.com/kiarashRezaei/VehicleCounting-YOLOv8-ByteTrack-IACV.git
    cd VehicleCounting-YOLOv8-ByteTrack-IACV
    ```

2. **Install dependencies**:

    Install the required Python packages using pip:

    ```bash
    pip install -r requirements.txt
    ```

3. **Set up ByteTrack**:

    The ByteTrack codebase is located in the `ByteTrack` folder. Follow the instructions in the `ByteTrack/README.md` to ensure it is correctly set up.

## Usage

### Running the Vehicle Counting System

To run the vehicle counting system on a video file:

1. **Run the main pipeline**:

    You can use the provided notebook (`Counting vehicles.ipynb`) or run the pipeline via the command line with the following:

    ```bash
    python countVehicles.py --video_path <path_to_video> --output <output_video_name>
    ```

    Example:

    ```bash
    python countVehicles.py --video_path ./input_videos/sample_video.mp4 --output ./output_videos/count_result.mp4
    ```

2. **Parameters**:
   - `video_path`: The path to the input video file.
   - `output`: The path to the output video showing the counted vehicles.
   - Other parameters such as `roi_xxyy` (Region of Interest) and tracking thresholds can be modified directly in the script.

## Results

The system was tested on several video sequences, showing high accuracy in detecting and counting vehicles. The combination of **YOLOv8** for detection and **ByteTrack** for tracking ensured reliable results, even in challenging scenarios involving occlusion and overlapping vehicles.

### Key Achievements:
- Accurate vehicle detection and tracking.
- Robust performance in occlusion and low-light scenarios.
- High processing speed suitable for real-time applications.

## Conclusion

This project demonstrates the successful implementation of a vehicle counting system using **YOLOv8** and **ByteTrack**. While the system performs well in most scenarios, some limitations remain, such as counting small or highly overlapped vehicles. Future improvements could focus on refining the tracking algorithm to handle edge cases more effectively.

