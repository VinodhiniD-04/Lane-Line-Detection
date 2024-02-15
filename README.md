# Lane-Line-Detection for self-driving cars on road
![image](https://github.com/VinodhiniD-04/Lane-Line-Detection/assets/135093669/d472f256-ef0d-4e3b-9bcc-6f664800abec)


## Overview
_________________________________________________________________________________________________

Lane line detection is a crucial component of autonomous driving systems, helping vehicles stay within their lanes and navigate safely. This project aims to detect lane lines on the road using computer vision techniques. It utilizes Python programming, Jupyter Notebook for development, Canny edge detection, Hough transform, and a Kaggle image dataset for training and testing.

## Key Features
_________________________________________________________________________________________________

* Detects lane lines on the road using computer vision techniques.
* Uses Canny edge detection to identify edges in the image.
* Applies the Hough transform to extract lines from the edge-detected image.
* Utilizes a Kaggle image dataset for training and testing the lane line detection algorithm.

## Requirements
_________________________________________________________________________________________________

### Hardware Requirements

* Computer/Server: Intel Core i5 or higher, 8 GB RAM

### Software Requirements

* Operating System: Windows
* Programming Languages: Python
* Integrated Development Environment: Jupyter Notebook
  
## Installation
_________________________________________________________________________________________________

* Clone the repository to your local machine.
* Install the necessary dependencies using pip or conda.
* Ensure the Kaggle image dataset is available in the correct directory.
* Open the Jupyter Notebook file and run the code cells to perform lane line detection.
  
## Usage
_________________________________________________________________________________________________

* Open the Jupyter Notebook file containing the lane line detection code.
* Run each code cell sequentially to perform edge detection, Hough transform, and lane line detection.
* Visualize the detected lane lines on the road image.

## Procedure
_________________________________________________________________________________________________

* Import required libraries
* Make_coordinates function: Generates endpoints of a line based on slope and intercept parameters.
* Average_slope_intercept function: Takes a set of lines, calculates their slopes and intercepts, separates them into left and right lanes based on slope sign, averages the parameters for each lane, and then uses these averaged parameters to generate the left and right lane lines.
* Canny function: Applies Canny edge detection after converting the image to HLS color space.
* Display_lines function: Creates an image with the detected lines drawn on it.
* Region_of_interest function: Defines a region of interest (ROI) in the image to focus on the area where lane lines are expected.
* The main script loads an image 'solidYellowLeft.jpg' (you can replace img using my test images file or can download dataset from kaggle), applies the series of image processing steps, detects Hough lines, averages and extrapolates them, and finally displays the original image with the detected lane lines overlaid.
