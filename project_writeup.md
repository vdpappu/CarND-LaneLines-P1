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
    

    
