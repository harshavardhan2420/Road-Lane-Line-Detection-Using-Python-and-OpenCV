## Road Lane Line Detection Using Python and OpenCV
## main.py file
## Table of Contents  

1. [Key Features](#key-features)  
2. [Technologies and Tools](#technologies-and-tools)  
3. [Project Workflow](#project-workflow)  
4. [Step-by-Step Explanation](#step-by-step-explanation)  
    - [1. Input Processing](#1-input-processing)  
    - [2. Region of Interest Selection](#2-region-of-interest-selection)  
    - [3. Edge Detection](#3-edge-detection)  
    - [4. Lane Detection](#4-lane-detection)  
    - [5. Dynamic Smoothing](#5-dynamic-smoothing)  
    - [6. Output Visualization](#6-output-visualization)  
5. [Installation](#installation)  
6. [Example Output](#example-output)  
7. [Applications](#applications)  
8. [Supporting Materials](#supporting-materials)  
9. [Keywords](#keywords)  

## Key Features  
- Real-Time Lane Detection: Detects lane lines on road frames in real-time.  
- Frame Masking: Filters irrelevant information to focus on the region of interest.  
- Hough Transform: Detects and highlights lane lines accurately.  
- Dynamic Smoothing: Reduces noise and ensures lane detection is smooth and continuous over frames.  
- Canny Edge Detection: Accurately identifies edges in images to assist in lane line detection.  

## Technologies and Tools  
- Programming Language: Python  
- Libraries:  
  - [OpenCV](https://opencv.org/): For computer vision operations.  
  - [NumPy](https://numpy.org/): For numerical computations.  
  - [MoviePy](https://zulko.github.io/moviepy/): For video processing and visualization.  
  - [Matplotlib](https://matplotlib.org/): For plotting and debugging.  

## Project Workflow  
1. Input processing of video or image frames.  
2. Define a region of interest (ROI) to filter unnecessary parts of the frame.  
3. Detect edges using Gaussian blur and Canny edge detection.  
4. Apply the Hough Line Transform to detect lane lines.  
5. Smooth lane line detection across frames for continuity.  
6. Overlay the detected lane lines on the original frame.  

## Step-by-Step Explanation  

### 1. Input Processing  
- Objective: Load a video or series of road images to process frame by frame.  
- Implementation:  
  - Convert the frame to grayscale using `cv2.cvtColor`.  
  - Extract relevant color ranges (e.g., yellow and white for lane lines) using HSV masks.  

### 2. Region of Interest Selection  
- Objective: Focus on the road section where lane lines are likely to be present.  
- *Implementation:  
  - Define a polygol region (ROI) based on road geometry.  
  - Apply masking to keep only the ROI using `cv2.bitwise_and`.  

### 3. Edge Detection  
- Objectve: Identify the edges in the ROI that represent potential lane boundaries.  
- Implementation:  
  - Apply Gaussian blur to reduce noise in the frame.  
  - Use Canny edge detection to highlight lane line edges.  

### 4. Lane Detection  
- Objective: Detect and segment lane lines from other edges.  
- Implementation:  
  - Use the Hough Line Transform to detect straight lines.  
  - Separate lines into left and right lanes based on slope.  

### 5. Dynamic Smoothing  
- Objective: Ensure the detected lane lines are smooth and consistent across frames.  
- Implementation:  
  - Use a weighted average of previous and current frame detections to smooth lane lines.  

### 6. Output Visualization  
- Objective: Overlay the detected lane lines on the original frame for visualization.  
- Implementation:  
  - Draw lane lines using `cv2.line`.  
  - Combine the lane lines with the original frame using `cv2.addWeighted`.  

---

## Installation  
1. Clone the repository:  
   ```bash  
   git clone https://github.com/your-username/real-time-lane-detection.git  
   ```  

2. Install required libraries:  
   ```bash  
   pip install numpy opencv-python matplotlib moviepy  
   ```  

3. Run the project on sample videos:  
   ```bash  
   python lane_detection.py  
   ```  

---

## Example Output  
The output is a video or frame sequence with lane lines clearly overlaid on the original road footage. Below is an example of lane detection in action:  

- Input: Video of a road captured from a dashboard camera.  
- Output: The lane lines are dynamically highlighted in real-time.  

## Applications  
- Autonomous vehicles for lane guidance and navigation.  
- Driver-assistance systems to alert drivers about lane deviations.  
- Research and development in intelligent transportation systems.  

---

## Supporting Materials  

### Tutorials and Articles  
- [Introduction to Lane Detection with OpenCV](https://learnopencv.com/road-lane-line-detection-with-openCV/)  
- [Understanding the Hough Transform](https://towardsdatascience.com/understanding-hough-transform-with-python-22db266355e8)  
- [Canny Edge Detection Explained](https://docs.opencv.org/3.4/da/d22/tutorial_py_canny.html)  

### Research Papers  
- [Lane Detection for Autonomous Vehicles](https://arxiv.org/abs/1802.05591)  
- [Improved Lane Detection Algorithms](https://www.sciencedirect.com/science/article/abs/pii/S0957417417305268)  

### Open Datasets  
- [Udacity Self-Driving Car Dataset](https://github.com/udacity/self-driving-car)  
- [KITTI Vision Benchmark Suite](http://www.cvlibs.net/datasets/kitti/)  

## Keywords  
Python, OpenCV, Computer Vision, Lane Detection, Self-Driving Cars, Hough Transform, Canny Edge Detection, Real-Time Processing  
