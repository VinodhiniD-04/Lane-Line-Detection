## Lane-Line-Detection for self-driving cars on road
Domain- Computer Vision
# import required libraries
import numpy as np
from google.colab.patches import cv2_imshow
from numpy.lib.function_base import average

# make_coordinates function: Generates endpoints of a line based on slope and intercept parameters.

def make_coordinates (image, line_parameters):
  slope, intercept = line_parameters
  print(image.shape)
  y1 = image.shape[0]
  y2 = int(y1*(3/5))
  x1 = int((y1-intercept)/slope)
  x2 = int((y2-intercept)/slope)
  return np.array([x1,y1,x2,y2])
  
# average_slope_intercept function: Takes a set of lines, calculates their slopes and intercepts, separates them into left and right lanes based on slope sign, averages the parameters for each lane, and then uses these averaged parameters to generate the left and right lane lines.

def average_slope_intercrept(image,line):
  left_fit = []
  right_fit = []
  for line in lines:
    x1,y1,x2,y2 = line.reshape(4)
    parameters = np.polyfit((x1,x2),(y1,y2),1)
    print(parameters)
    slope = parameters[0]
    intercept = parameters[1]
    if slope < 0:
      left_fit.append((slope,intercept))
    else:
      right_fit.append((slope,intercept))
  left_fit_average = np.average(left_fit,axis=0)
  right_fit_average = np.average(right_fit,axis=0)
  left_line = make_coordinates(image,left_fit_average)
  right_line = make_coordinates(image,right_fit_average)
  return np.array([left_line, right_line])
  
# canny function: Applies Canny edge detection after converting the image to HLS color space.

def canny(image):
  hls = cv2.cvtColor(image,cv2.COLOR_BGR2HLS)
  blur = cv2.GaussianBlur(hls,(5,5),0)
  return canny

# display_lines function: Creates an image with the detected lines drawn on it.

def display_lines (image,lines):
  line_image = np.zeros_like(image)
  if lines is not None:
    for line in lines:
      x1, y1, x2, y2 = line.reshape(4)
      cv2.line(line_image,(x1,y1),(x2,y2),(255,0,0),10)
  return line_image

# region_of_interest function: Defines a region of interest (ROI) in the image to focus on the area where lane lines are expected.

def region_of_interest(lane_image):
  height = lane_image.shape[0]
  triangle = np.array([[(0,height),(900,height),(500,260)]])
  mask = np.zeros_like(lane_image)
  cv2.fillPoly(mask, triangle,255)
  masked_image = cv2.bitwise_and(lane_image,mask)
  return masked_image

# The main script loads an image 'solidYellowLeft.jpg' (you can replace img using my test images file or can download dataset from kaggle), applies the series of image processing steps, detects Hough lines, averages and extrapolates them, and finally displays the original image with the detected lane lines overlaid.

image= cv2.imread('mv solidYellowLeft.jpg')
lane_image = np.copy(image)
canny_image = canny(lane_image)
cropped_image = region_of_interest(canny_image)
rho = 2 
theta = np.pi/180 
threshold = 100   
min_line_length = 40 
max_line_gap = 30 
lines = cv2.HoughLinesP(cropped_image, rho, theta, threshold, np.array([]),min_line_length,max_line_gap)
averaged_lines = average_slope_intercrept(lane_image,lines)
line_image = display_lines(lane_image, averaged_lines)
combo_image = cv2.addWeighted(lane_image, 0.8, line_image,1,1)
