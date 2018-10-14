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

### Camera Calibration

Camera calibration images are extracted. 
Perform a loop operation across all the calibration images to extract all mtx and dist parameters:
![imagen](https://user-images.githubusercontent.com/41348711/46917754-bb72b380-cfca-11e8-99f0-86c789885039.png)
Use mtx and dist parameters to undistort any image taken with that camera:
![imagen](https://user-images.githubusercontent.com/41348711/46917783-08568a00-cfcb-11e8-907a-1fca755bfb69.png)

![imagen](https://user-images.githubusercontent.com/41348711/46917671-e14b8880-cfc9-11e8-9299-165012fee99e.png)


### Unwrap images

A function is generated to unwrap the images. To do so I just selected 4 points that define a rectangle in a straight line picture

![imagen](https://user-images.githubusercontent.com/41348711/46917728-69ca2900-cfca-11e8-9a51-258d33244f74.png)
