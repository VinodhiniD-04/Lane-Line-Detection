# Lane-Line-Detection for self-driving cars on road
![image](https://github.com/VinodhiniD-04/Lane-Line-Detection/assets/135093669/fa85207a-9018-44dc-a1c2-02ebd6d14c25)

__________________________________________________________
# dependencies
* Python 3.5
* NumPy
* OpenCV
* Canny edge detection
* Hough Transform
__________________________________________________________
# project steps
* Import required libraries
* Make_coordinates function: Generates endpoints of a line based on slope and intercept parameters.
* Average_slope_intercept function: Takes a set of lines, calculates their slopes and intercepts, separates them into left and right lanes based on slope sign, averages the parameters for each lane, and then uses these averaged parameters to generate the left and right lane lines.
* Canny function: Applies Canny edge detection after converting the image to HLS color space.
* Display_lines function: Creates an image with the detected lines drawn on it.
* Region_of_interest function: Defines a region of interest (ROI) in the image to focus on the area where lane lines are expected.
* The main script loads an image 'solidYellowLeft.jpg' (you can replace img using my test images file or can download dataset from kaggle), applies the series of image processing steps, detects Hough lines, averages and extrapolates them, and finally displays the original image with the detected lane lines overlaid.
