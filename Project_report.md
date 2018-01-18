# **Finding Lane Lines on the Road** 

## Overview

Human eyes help them to detect the lane lines and consequently help them to steer the vehicle. Similary, cameras and sensors act as eyes for a vehicle to drive autonomously. The first step in developing a autonomous driving car would be to detect lane lines automatically in images and videos using an algorithm which is implemented using python and openCV.Techniques of Canny edge detection and hough transform are used to detect lane lines on the road.

---

### Goals/Steps
* Make a pipeline that finds lane lines on the road
* Reflection of work in a written report


---

### Reflection

#### 1. Process(Pipeline) :

My pipeline consisted of 6 steps as follows: 
1. Converting to grayscale and Gaussian smoothing : First, I considered one image and converted it to grayscale, then I applied Gaussian blur to it for suppressing noise and spurious gradients.
![Image of gaussian output](/test_images_output/blur_gray.jpg)


2. Applying Canny Edge detection: Applying OpenCV Canny function , I detected all the edges in the image. The output of this function gives the edges in white and black everywhere else in the image as follows-  
![Image of Edge output](/test_images_output/edges.jpg)


3. Selecting Region of Interest: For removing unnecessary edges in the image, I selected a particular region using OpenCV fillpoly() function. The output is detected segments of the lane lines as follows-
![Image of after selecting ROI](/test_images_output/masked_edges.jpg)


4. Detecting straight lane lines using Hough Transform: Then applying OpenCV HoughLinesP() function I found the straight lines and draw those lines using draw_lines() function. I have tuned some parameters like threshold, min_line_len and max_line_gap to connect small segments to a long straight lines and remove any errors. Finally displaying or saving the image.

![Image of segments output](/test_images_output/lines_image.jpg)



5. Modifying draw_lines() function: While testing on most of the images, the detected lane lines where like small segments and most of the lines were not reaching the base of the image. So , for extending the lines and drawing one average line on both lane sides, I modified the draw_lines() function as follows:
   - First I calculated slope of each line and distinguished them into left and right
   - Then I calculated the bottom x intercepts using shape of image and equation of line  <img src="https://latex.codecogs.com/svg.latex?\Large&space;y-y1=m(x-x1)" title="line" />
   - Calculated average bottom x-intercept and average slope for each side lines
   - Calculated top x-intercepts modifying <img src="https://latex.codecogs.com/svg.latex?\Large&space;m=\frac{y2-y1}{x2-x1}" title="slope" />
   - Now that I have all the points I used that for drawing left and right lines with line() function
   
![Image of segments output](/test_images_output/lines_edges.jpg)

   
6. Drawing lanes over videos and adjusting parameters : While testing on videos, I found out that some of the lines where going out of the lane scope especially for solidYellowLeft sample video due to horizontal lines at some points in the video. For this reason I further modified my draw_lines() function so that such horizontal lines are ignored while calculating average line.







#### 2. Potential shortcomings :


One potential shortcoming would be what would happen when the lane is more curved or have a sharp turn. 

Another shortcoming could be that the lane may fall out of region of interest.




#### 3. Possible improvements :

A possible improvement would be to automatically find the region of interest so that this algorithm becomes more robust. 

