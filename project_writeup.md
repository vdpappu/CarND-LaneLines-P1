#**Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

##Pipeline Overview
Current pipeline consists of five steps:<br>
<br>
<b>Grey scale Conversion:</b><br>
* This step involves converting the image from RGB to single color channel image
* Grey scale conversion is an essential pre-processing step for most of the image processing problems

<br>
<b>Edge/Boundary detection using Canny Algorithm:</b><br>
This step involves identifying the edges/boundaries of object of interest in the image using canny edge detection algorithm, 
this involves following steps
  * Compute the gradient of previoulsy grey-scale converted image
  * Identify the edges in the range of low amd high gradient thresholds of choice
  * Inorder to reduce noise and misleading gradients, we apply gaussian smooothing to the image before edge detection
    * This involves averaging the pixel values over a patch of image

Gaussian smooting and edge detection involves experimenting with following parameters that suits the current requirement:
  * Patch size for Gaussian smoothing
  * Upper threshold for gradient
  * Lower threshold for gradient
  
<br>
<b>Region of interest identification</b><br>
This step involves extracting the patch of image where our object of interest lies - lane lines in this case
  * Assuming that the camera is mounted at a fixed position, fixed coordinates of the lanes were experimented and identified
 
<br>
<b>Hough transformation for line detection</b><br>
This step involves finding lines from the edges identified in previous step. Hough transform was used for the same
Applying Hough transformation involves experimenting with following turning parameters:
  * rho - perpendicular distance of line from origin
  * theta - angle of the line
  * threshold - minimum number of intersecting lines in a Hough space grid 
  * min_line_length - minimum lenght of line to be identified
  * max_line_gap - maximum dsitance between lines to merge two near by lines

<br>
<b>Overlaying Hough lines onto the original image</b><br>
This step involves overlaying the Hough lines identified in previous step onto the original image

<br>
<b>Improving draw_lines() function to draw single solid line over the left and right lanes</b><br>
Following approach was taken to solve this problem
  * Find the slope of Hough line to find if it is on the left or right lane
  * Identify end points of the first and last lines on each lane
  * Draw solid line from the end points as required (example shown below)
[//]: # (Image References)

[image1]: ./IMG_20170225_220040.jpg "Solid_Line"
![alt text][image1]

 

##Limitations of current pipeline<br>
 * The tunable parameters are experimented based on the images/videos provided, this may not generalize
 * Region of interest calculation may fail on roads curvy roads
 * Current pipeline may fail at detecting the lane lines in low visibility settings
<br>

##Suggested Improvements<br>
 * Running the pipeline on more images/videos to tune the parameters could yield better results
 * Region of interest calculation that can cover corner cases
 * Improving the Edge detection and Hough transformation modules that are sensitive enough to find the lane lines in low visibility conditions (experimentation and finding the right combination of parameters)
