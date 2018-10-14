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
Perform a loop operation across all the calibration images to extract all mtx and dist parameters.

for fname in images:
    img = cv2.imread(fname) #read images in BGR format
    gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY) #change image color space: from BGR to Gray
    # Find the chessboard corners
    ret, corners = cv2.findChessboardCorners(gray,(9,6),None)
    # If found, add object points, image points
    if ret == True:
        objpoints.append(objp)
        imgpoints.append(corners)
        # Draw and display the corners
        # img = cv2.drawChessboardCorners(img, (9,6), corners, ret)
ret, mtx, dist, rvecs, tvecs = cv2.calibrateCamera(objpoints, imgpoints, gray.shape[::-1], None, None)



Use mtx and dist parameters to undistort any image taken with that camera:

def undistort(img,mtx,dist):
    undistorted=cv2.undistort(img, mtx, dist, None, mtx)
    return undistorted
