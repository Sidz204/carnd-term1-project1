# **Finding Lane Lines on the Road** 

## Overview

Human eyes help them to detect the lane lines and consequently help them to steer the vehicle. Similary, cameras and sensors act as eyes for a vehicle to drive autonomously. The first step in developing a autonomous driving car would be to detect lane lines automatically in images and videos using an algorithm which is implemented using python and openCV.Techniques of Canny edge detection and hough transform are used to detect lane lines on the road.

---

### Goals/Steps
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


---

### Reflection

#### 1. Process(Pipeline) :

My pipeline consisted of 6 steps as follows: 
1. Converting to grayscale and Gaussian smoothing : First, I considered one image and converted it to grayscale, then I applied Gaussian blur to it for suppressing noise and spurious gradients.

2. Applying Canny Edge detection:


3. Selecting Region of Interest:

4. Detecting straight lane lines using Hough Transform:

5. Modifying draw_lines() function:

6. Drawing lanes over videos and adjusting parameters : 






First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Potential shortcomings :


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Possible improvements :

A possible improvement would be to ...

Another potential improvement could be to ...
