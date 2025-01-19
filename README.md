### LinkedIn Post

🚗🔍 **Smart Parking Space Detector** 🚗🔍  

Excited to share my recent project where I developed a **Parking Space Detection System**!  

🔑 **Features:**  
- The system detects parking spaces using a **real-time video feed** and highlights vacant spaces in **green** and occupied spaces in **red**.  
- Displays the total number of available parking spaces in the output image.  

⚙️ **Technical Highlights:**  
1️⃣ **Image Preprocessing**:  
   - Converted frames to grayscale for simplicity and efficiency.  
   - Applied Gaussian Blur to reduce noise and enhance edge detection.  
   - Used Adaptive Thresholding and Median Blur to create a clean binary image for parking space detection.  

2️⃣ **Object Detection**:  
   - Extracted regions corresponding to parking spaces and counted the number of non-zero pixels to determine if the space is occupied.  
   - Dynamically updated bounding boxes and vacancy counts on the frame.  

📊 **Tools Used:**  
- OpenCV for image processing and video handling.  
- Python for developing the end-to-end system.  

💻 **Output:**  
Check out the image below! Green rectangles indicate free spaces, red rectangles indicate occupied ones, and the live count of vacant spaces is displayed on the frame.  

---

### Resume Entry

**Smart Parking Space Detector**  
*Technologies: Python, OpenCV, Computer Vision*  

- Designed and implemented a parking space detection system capable of dynamically identifying free and occupied parking spaces from a video feed.  
- Utilized OpenCV for real-time image preprocessing and object detection, including techniques like grayscale conversion, Gaussian Blur, and Adaptive Thresholding.  
- Extracted predefined parking space regions, analyzed pixel densities, and dynamically updated bounding boxes and free space counts on video frames.  
- Achieved a robust detection pipeline with clear visual indicators (green for vacant, red for occupied) and a real-time count of available spaces.  

---

### README.md

# Smart Parking Space Detection System 🚗

This project is a parking space detection system that dynamically identifies free and occupied parking spaces from a real-time video feed. It uses OpenCV for image processing and Python for implementation.

## Features
- Detects parking spaces in real-time from video.
- Highlights vacant spaces with **green** rectangles and occupied spaces with **red** rectangles.
- Displays the count of available parking spaces on the video frame.

## Demo
Insert your output image here.

## Prerequisites
- Python 3.x
- OpenCV library
- cvzone library
- NumPy

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ParkingSpaceDetection.git
   cd ParkingSpaceDetection
   ```
2. Install the required libraries:
   ```bash
   pip install opencv-python cvzone numpy
   ```

## How It Works
1. **Setup Parking Spaces (`ParkingSpacePicker.py`)**
   - Open `ParkingSpacePicker.py` and select parking spaces by clicking on the video.
   - Save the parking space coordinates for processing.

2. **Real-Time Detection (`main.py`)**
   - Processes the video feed to detect free and occupied parking spaces.
   - Converts frames to grayscale, applies Gaussian Blur, Adaptive Thresholding, and other preprocessing steps for accurate detection.
   - Dynamically updates bounding boxes and displays the vacancy count.

## How to Run
1. Run `ParkingSpacePicker.py` to set up parking space positions:
   ```bash
   python ParkingSpacePicker.py
   ```
   - Left-click to add a parking space.  
   - Right-click to remove a parking space.

2. Run the main detection system:
   ```bash
   python main.py
   ```
   - This will start processing the video and display the real-time detection results.

## Technical Details
1. **Image Preprocessing:**
   - Converted frames to grayscale using:
     ```python
     imgGray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
     ```
   - Applied Gaussian Blur to reduce noise:
     ```python
     imgBlur = cv2.GaussianBlur(imgGray, (3, 3), 1)
     ```
   - Used Adaptive Thresholding for binary segmentation:
     ```python
     imgThreshold = cv2.adaptiveThreshold(
         imgBlur, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY_INV, 25, 16)
     ```
   - Smoothed the binary image using Median Blur and dilation:
     ```python
     imgMedian = cv2.medianBlur(imgThreshold, 5)
     imDilate = cv2.dilate(imgMedian, kernel, iterations=1)
     ```

2. **Parking Space Detection:**
   - Extracted predefined regions for each parking space and counted non-zero pixels:
     ```python
     count = cv2.countNonZero(imgCrop)
     ```
   - Updated bounding boxes dynamically based on occupancy:
     ```python
     if count < 900:
         color = (0, 255, 0)
     else:
         color = (0, 0, 255)
     ```

## Output
- Vacant spaces are shown in **green**.  
- Occupied spaces are shown in **red**.  
- Live count of available spaces is displayed on the frame.

## License
This project is licensed under the MIT License.

