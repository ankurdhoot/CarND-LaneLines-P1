# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "Solid White Curve"
[image2]: ./test_images_output/solidWhiteCurve.jpg "Solid White Curve With Lane Lines"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

First, I converted the images to grayscale and applied a Gaussian blur.

Then, I applied Canny edge detection to the gray and blurred image followed by selection of a polygonal
area of the image likely to contain the lane lines. 

Then, the Hough transform is applied to find the start and end points of each edge segment. 

I then use the sign of the slope of the edge segment to determine whether the points on the edge belongs
to the left or right lane line.

I then fit a degree one (i.e line) polynomial to the set of points belonging to each lane line and draw the
resulting lines on the original image.

![alt text][image1]

![alt text][image2]

### 2. Identify potential shortcomings with your current pipeline


There are multiple shortcomings of the current solution:

1) Assumption that lane lines will always be centered on the image
2) Assumption that the sign of the slope can differentiate left vs right lane lines
3) As can be seen in the challenge.mp4, the pipeline falls apart under poor lighting. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use CNNs to detect the left lane line and right lane line.
Or, since the ultimate purpose is to steer a car, we could predict a steering angle based on
the current frame. 
