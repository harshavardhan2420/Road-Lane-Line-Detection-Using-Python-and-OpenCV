# Road Lane Line Detection Using Python and OpenCV
## main.py file
### Table of Contents  

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
5. [Example Output](#example-output)  
6. [Applications](#applications)  
7. [Supporting Materials](#supporting-materials)  
8. [Keywords](#keywords)  

### Key Features  
- Real-Time Lane Detection: Detects lane lines on road frames in real-time.  
- Frame Masking: Filters irrelevant information to focus on the region of interest.  
- Hough Transform: Detects and highlights lane lines accurately.  
- Dynamic Smoothing: Reduces noise and ensures lane detection is smooth and continuous over frames.  
- Canny Edge Detection: Accurately identifies edges in images to assist in lane line detection.  

### Technologies and Tools  
- Programming Language: Python  
- Libraries:  
  - [OpenCV](https://opencv.org/): For computer vision operations.  
  - [NumPy](https://numpy.org/): For numerical computations.  
  - [MoviePy](https://zulko.github.io/moviepy/): For video processing and visualization.  
  - [Matplotlib](https://matplotlib.org/): For plotting and debugging.  

### Project Workflow  
1. Input processing of video or image frames.  
2. Define a region of interest (ROI) to filter unnecessary parts of the frame.  
3. Detect edges using Gaussian blur and Canny edge detection.  
4. Apply the Hough Line Transform to detect lane lines.  
5. Smooth lane line detection across frames for continuity.  
6. Overlay the detected lane lines on the original frame.  

## Step-by-Step Explanation  

#### 1. Input Processing  
- Objective: Load a video or series of road images to process frame by frame.  
- Implementation:  
  - Convert the frame to grayscale using `cv2.cvtColor`.  
  - Extract relevant color ranges (e.g., yellow and white for lane lines) using HSV masks.  

#### 2. Region of Interest Selection  
- Objective: Focus on the road section where lane lines are likely to be present.  
- *Implementation:  
  - Define a polygol region (ROI) based on road geometry.  
  - Apply masking to keep only the ROI using `cv2.bitwise_and`.  

#### 3. Edge Detection  
- Objectve: Identify the edges in the ROI that represent potential lane boundaries.  
- Implementation:  
  - Apply Gaussian blur to reduce noise in the frame.  
  - Use Canny edge detection to highlight lane line edges.  

#### 4. Lane Detection  
- Objective: Detect and segment lane lines from other edges.  
- Implementation:  
  - Use the Hough Line Transform to detect straight lines.  
  - Separate lines into left and right lanes based on slope.  

#### 5. Dynamic Smoothing  
- Objective: Ensure the detected lane lines are smooth and consistent across frames.  
- Implementation:  
  - Use a weighted average of previous and current frame detections to smooth lane lines.  

#### 6. Output Visualization  
- Objective: Overlay the detected lane lines on the original frame for visualization.  
- Implementation:  
  - Draw lane lines using `cv2.line`.  
  - Combine the lane lines with the original frame using `cv2.addWeighted`.  

---

### Example Output  
The output is a video or frame sequence with lane lines clearly overlaid on the original road footage. Below is an example of lane detection in action:  

- Input: Video of a road captured from a dashboard camera.  
- Output: The lane lines are dynamically highlighted in real-time.  

### Applications  
- Autonomous vehicles for lane guidance and navigation.  
- Driver-assistance systems to alert drivers about lane deviations.  
- Research and development in intelligent transportation systems.  

---

### Supporting Materials  

#### Tutorials and Articles  
- [Introduction to Lane Detection with OpenCV](https://learnopencv.com/road-lane-line-detection-with-openCV/)  
- [Understanding the Hough Transform](https://towardsdatascience.com/understanding-hough-transform-with-python-22db266355e8)  
- [Canny Edge Detection Explained](https://docs.opencv.org/3.4/da/d22/tutorial_py_canny.html)  

#### Research Papers  
- [Lane Detection for Autonomous Vehicles](https://arxiv.org/abs/1802.05591)  
- [Improved Lane Detection Algorithms](https://www.sciencedirect.com/science/article/abs/pii/S0957417417305268)  

#### Open Datasets  
- [Udacity Self-Driving Car Dataset](https://github.com/udacity/self-driving-car)  
- [KITTI Vision Benchmark Suite](http://www.cvlibs.net/datasets/kitti/)  

### Keywords  
Python, OpenCV, Computer Vision, Lane Detection, Self-Driving Cars, Hough Transform, Canny Edge Detection, Real-Time Processing  


## gui.py file 

A GUI-based application to showcase real-time lane detection. Using **Tkinter** for the GUI and **OpenCV** for video processing, it demonstrates input and output video streams for lane-line detection in a user-friendly interface.  

### Table of Contents  

1. [Key Features](#key-features)  
2. [Technologies and Tools](#technologies-and-tools)  
3. [Project Workflow](#project-workflow)  
4. [Step-by-Step Explanation](#step-by-step-explanation)  
    - [1. Setting Up the GUI](#1-setting-up-the-gui)  
    - [2. Integrating Input Video](#2-integrating-input-video)  
    - [3. Displaying Processed Video](#3-displaying-processed-video)  
    - [4. Quit Button Implementation](#4-quit-button-implementation)   
5. [Example Output](#example-output)  
6. [Applications](#applications)  
7. [Supporting Materials](#supporting-materials)  

### Key Features  

- Real-Time Display: Simultaneously displays input and output video streams side by side in the application window.  
- Dynamic Resizing: Adjusts video frame sizes to fit the GUI layout.  
- User-Friendly GUI: Built using Tkinter, providing an intuitive interface with a title, logo, and Quit button.  

---

### Technologies and Tools  

- Programming Language: Python  
- Libraries:  
  - [Tkinter](https://docs.python.org/3/library/tkinter.html): For creating the graphical user interface.  
  - [OpenCV](https://opencv.org/): For video processing and manipulation.  
  - [Pillow](https://pillow.readthedocs.io/): For handling images in the Tkinter GUI.  
  - [NumPy](https://numpy.org/): For numerical operations on video frames.  

---

### Project Workflow  

1. Import necessary libraries and set up the global variables for video streams.  
2. Design the GUI using Tkinter and embed the application logo, title, and placeholders for video streams.  
3. Integrate OpenCV to process and display the input and processed video streams in real-time.  
4. Add functionality for exiting the application with a Quit button.  

---

### Step-by-Step Explanation  

#### 1. Setting Up the GUI  

- Objective: Create a Tkinter-based application window to hold all components like video displays and buttons.  
- Implementation:  
  - Use `Tk()` to create the main window and set the title and dimensions.  
  - Add a heading and a logo at the top using `Label()`.  
  - Use `pack()` to organize elements within the window.  

```python  
root = tk.Tk()  
img = ImageTk.PhotoImage(Image.open("logo.png"))  
heading = Label(root, image=img, text="Lane-Line Detection")  
heading.pack()  
heading2 = Label(root, text="Lane-Line Detection", pady=20, font=('arial', 45, 'bold'))  
heading2.pack()  
```  
#### 2. Integrating Input Video  

- Objective: Load an input video stream and display it in the GUI.  
- Implementation:  
  - Open the video stream using OpenCV's `VideoCapture()`.  
  - Read frames from the video and resize them using `cv2.resize()`.  
  - Convert the frames from BGR to RGB and display them in the Tkinter window using `ImageTk.PhotoImage()`.  

```python  
cap1 = cv2.VideoCapture("./input2.mp4")  

def show_vid():  
    flag1, frame1 = cap1.read()  
    frame1 = cv2.resize(frame1, (600, 500))  
    if flag1:  
        pic = cv2.cvtColor(frame1, cv2.COLOR_BGR2RGB)  
        img = Image.fromarray(pic)  
        imgtk = ImageTk.PhotoImage(image=img)  
        lmain.imgtk = imgtk  
        lmain.configure(image=imgtk)  
        lmain.after(10, show_vid)  
```  

#### 3. Displaying Processed Video  

- Objective: Show the output video stream with lane detection applied.  
- Implementation:  
  - Open the processed video using another `VideoCapture()` object.  
  - Follow the same steps as the input video for resizing and display.  

```python  
cap2 = cv2.VideoCapture("./output2.mp4")  

def show_vid2():  
    flag2, frame2 = cap2.read()  
    frame2 = cv2.resize(frame2, (600, 500))  
    if flag2:  
        pic2 = cv2.cvtColor(frame2, cv2.COLOR_BGR2RGB)  
        img2 = Image.fromarray(pic2)  
        img2tk = ImageTk.PhotoImage(image=img2)  
        lmain2.img2tk = img2tk  
        lmain2.configure(image=img2tk)  
        lmain2.after(10, show_vid2)  
```  

#### 4. Quit Button Implementation  

- Objective: Provide a way to exit the application.  
- Implementation:  
  - Add a `Button()` widget with the `command` set to `root.destroy`.  
  - Position the button using `pack()` with the `side=BOTTOM` parameter.  

```python  
exitbutton = Button(root, text='Quit', fg="red", command=root.destroy).pack(side=BOTTOM)  
```  
   
### Example Output  

The application window will display the input video on the left and the processed output video with detected lane lines on the right.  

## Applications  

- Showcasing lane-line detection projects in a GUI format.  
- Educational tools for computer vision and GUI programming.  
- Prototyping for autonomous driving systems.  

---

### Supporting Materials  

- [Tkinter Documentation](https://docs.python.org/3/library/tkinter.html)  
- [OpenCV Tutorials](https://opencv-python-tutroals.readthedocs.io/en/latest/)  
- [Pillow Documentation](https://pillow.readthedocs.io/)  
