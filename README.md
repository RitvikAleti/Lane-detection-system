# Lane Detection System with Python and OpenCV

## Introduction

This project demonstrates the development of a lane detection system using computer vision techniques, Python, and OpenCV. Lane detection is a critical component of self-driving cars and advanced driver-assistance systems (ADAS), as it provides a constant reference for the vehicle's position on the road.

## Challenges in Road Lane Detection

Detecting road lanes presents several challenges, including:

- Converting images to grayscale for better processing.
- Reducing noise using Gaussian blur.
- Applying Canny edge detection.
- Isolating lane lines in the image.
- Using Hough line transform to detect lines in the isolated region.
- Averaging and displaying the detected lane lines.

## Getting Started

Ensure you have OpenCV installed, and install the necessary libraries such as NumPy and Matplotlib for image processing. Use the following command to install the required packages:

```bash
pip install opencv-python-headless numpy matplotlib
```

Preprocessing of Images
-----------------------

### Grayscale Conversion

Images are converted to grayscale to simplify image processing. Grayscale images have lower complexity than color images, making it easier to detect lane lines.

### Gaussian Blur

A Gaussian blur is applied to reduce noise in the image. Noise can interfere with Canny edge detection, so it's crucial to minimize noise.

### Canny Edge Detection

Canny edge detection is used to detect sharp changes in luminosity, identifying edges in the image. This process includes noise reduction, intensity gradient, non-maximum suppression, and hysteresis thresholding.

### Isolating Lane Lines

A region of interest is defined to isolate the lane lines in the image. This region is typically a trapezoidal area near the bottom of the image, where the lane lines are expected to appear.

Hough Line Transform
--------------------

The Hough line transform is the core of the algorithm, converting clusters of white pixels from the isolated region into actual lines. This process involves defining parameters like rho, theta, minimum intersections, and line length.

Optimizing and Displaying Lines
-------------------------------

### Averaging Lines

The `average` function takes the line segments detected by `cv2.HoughLinesP` and calculates the average slope and y-intercept for the left and right lines. The left lines typically have negative slopes, while the right lines have positive slopes. The `make_points` function defines the start and endpoints for the lines.

### Displaying Lines

The `display_lines` function takes the image and the calculated line coordinates and overlays them on a black background, making the lane lines stand out. The `cv2.addWeighted` function darkens the original image to enhance visibility.

Running the Lane Detection System
---------------------------------

To run the lane detection system, execute the Python script:

'''
python lane_detection.py -i input_image.jpg
'''

Replace input_image.jpg with the path to your image or video file.
