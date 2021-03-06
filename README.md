# SDCND_Advance_Lane_Finding
Advance_Lane_Finding

The goals / steps of this project are the following:

* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply a distortion correction to raw images.
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view").
* Detect lane pixels and fit to find the lane boundary.
* Determine the curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

## Camera Calibration

Camera calibration images are extracted. 
Perform a loop operation across all the calibration images to extract all mtx and dist parameters:

![imagen](https://user-images.githubusercontent.com/41348711/46917754-bb72b380-cfca-11e8-99f0-86c789885039.png)

Use mtx and dist parameters to undistort any image taken with that camera:

![imagen](https://user-images.githubusercontent.com/41348711/46917671-e14b8880-cfc9-11e8-9299-165012fee99e.png)


## Unwrap images

A function is generated to unwrap the images. To do so I just selected 4 points that define a rectangle in a straight line picture

![imagen](https://user-images.githubusercontent.com/41348711/46917783-08568a00-cfcb-11e8-907a-1fca755bfb69.png)

![imagen](https://user-images.githubusercontent.com/41348711/46917728-69ca2900-cfca-11e8-9a51-258d33244f74.png)

## Define Filter functions

I used below functions (all given in the course):

* Absolute threshold (x & y): Extract from the greysclaed image the sobel X values in the range 20-250
* Magnitude threshold: Form the greyscaled image extract the values whose aboslute magnitude threshold (X & Y) is inside the range 30 to 100
* Direction threshold: As recommended in the course I checked in the range 0.7 to 1.3
* Saturation threshold: Converting the image to HSV color space and extracting Saturation values on the range from 120 to 255
* Red color threshold: Using the RGB color image, extract the Red values in the range from 200 to 255

![imagen](https://user-images.githubusercontent.com/41348711/46918965-a56bef80-cfd8-11e8-8f1a-476af966436a.png)

![imagen](https://user-images.githubusercontent.com/41348711/46918987-cd5b5300-cfd8-11e8-9436-57254896fef1.png)

After some tuning ans some trials I defined my pipeline function: 

![imagen](https://user-images.githubusercontent.com/41348711/46919002-17443900-cfd9-11e8-82c5-0a34f66d0802.png)

## Find the lane pixels and curve fitting 

Once the binary image is generated, it is passed through the Find_lane_pixels function. This function splits the image vertically to and uses histograms to locate the lane pixels. 
When located, they are aproximated to a 2nd degree curve using the fit_poly function:

![imagen](https://user-images.githubusercontent.com/41348711/46919104-8cfcd480-cfda-11e8-8e12-a00edeae6c58.png)

Both functions (find_lane_pixels & fit_poly) are copied from the course content

## Measure the radius of the curves

To do so I used the function given in the course and tunned the meter per pixel parameters:

![imagen](https://user-images.githubusercontent.com/41348711/46919167-90449000-cfdb-11e8-8bf9-e1487adc0b49.png)

## Define the process image function
this function mainly:
* Integrates the lane finding function with the radius and offset lane calculation 
* Plots both lanes and fill the are in between them 
* Prints the radius and the offset at the top of the image

![imagen](https://user-images.githubusercontent.com/41348711/46919222-7e172180-cfdc-11e8-9f82-6e9455d610b5.png)

## Apply to the project video

Using a similar pipeline to the one used in the first project, video images are extracted and process image function is applied to each frame of the video. Even I had no time to perform the line class and the function fit using previous fit the detection seems to work properly. 

![imagen](https://user-images.githubusercontent.com/41348711/46919236-cd5d5200-cfdc-11e8-8bc2-89295dcc369e.png)




