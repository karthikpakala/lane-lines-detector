# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />


[//]: # (Image References)

[image1]: ./my_pipeline.png 

[image1]: ./yellow_fail_frame.png 


Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project lane lines in images will be detected using Python and OpenCV. OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

The Project Pipeline
---
Generally, my pipeline for this lane detection project consists 6 steps:

1. Apply mask to select just pixels with yellow or white colour to detect the lanes
2. Convert image to grayscale and apply slight Gaussian Blur.
3. Apply Canny Edge Detector to get Edges 
4. Apply polygon mask to select region of interest
5. Perform Hough Lines transformation to get lines on the image. Extrapolate and average   
   the Hough lines to get a single solid line for each lane
6. Draw both lane lines on original image and add Weight


Here is the result for the whiteCarLaneSwitch.jpg image:

![alt text][image1]


To make the pipeline work for videos, moviepy.editor and IPython.display libraries have to be imported. A video is basically just a series of images. 
The exact details and python code descriptions can be found in the notebook P1_Lane_Lines.ipnyb.


Shortcomings
---
My major problem in this project was to perform the step 5 properly, especially to extrapolate and average the Hough Lines. The code also didn't quite work for the challenge video. The lane was also falsely detected in a frame of the solidYellowLeft.mp4 (11 seconds in). I also spend qutie a lot of time tuning the parameters for the hough lines, which also do not work very well for curved lane lines (see challenge.mp4). 

![alt text][image2]


Possible improvements
---
1. Tune the parameters for the Canny Edge Detector and Hough Lines using GUI Tool which are available online to make it more accurate and efficient.
 
2. Review the code and do debugging to find the cause of the falsely detected lane lines in some frames of the videos. Averaging lines might not be a good strategy and weighted average might need to be introduced.

3. Improve the code by doing advanced lane line detection techniques which includes consideration of image perspective and curvature among other things.

