# Car Parking Count

This project is a parking space detection system that dynamically identifies free and occupied parking spaces from a real-time video feed. It uses OpenCV for image processing and Python for implementation.

## Features
- Detects parking spaces in real-time from video.
- Highlights vacant spaces with **green** rectangles and occupied spaces with **red** rectangles.
- Displays the count of available parking spaces on the video frame.

## Prerequisites
- Python 
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


