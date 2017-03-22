# **Finding Lane Lines on the Road** 

## Writeup

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidYellowLeft.jpg

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted 4 steps.
1. I converted the input images to grayscale, applying Gaussian smoothing and Canny edge detection, then I apply Hough Transform to detect line.
2. In the detect lines, I obtain right lane candidate and left lane candidate based on the angle of line. (get_lane_lines())
3. I approximate the linear equation of each lanes from the candidates. (find_lane_line())
4. Finally, I draw the line fron the front of the input to center(y=320) using linear equation of each lanes.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function to create large and small points on elements of x at the start and end points in lines. based draw lines using these 4 points. 

Here is result of applying pipeline function: 
![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline
- Current pipeline and parameters is tailored to test_image and test_videos. Therefore, it is difficult to deal with short straight roads and curves.
- If cars are lined up like a traffic jam, lane detection becomes difficult.

### 3. Suggest possible improvements to your pipeline
A possible improvement would be as follows.
- Create a pipeline to detect the curves.
- Even if the detected lane is short, predict the appropriate lane.