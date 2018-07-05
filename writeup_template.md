# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of following steps:
1. Convert to grayscale image
2. Apply gaussian blur with kernel size of 3
3. Use Canny Edge Detection with correct high and low thresholds
4. Apply Region of Interest to remove unwanted edges
5. Obtain a list of hough lines within a region of interest 
6. Display overlapped original image and image containing hough lines


For drawing lines on left and right lanes, I modified the draw lines function as follows:
1. Divided the lines into right and left slopes(m) and intercepts (c) based on equation 
Y = mx + c
2. For all the hough lines, I calculated the slope of the lines and intercept of the line
3. Divided in to left and right lines based on slope. If the slope was negative the line belonged to left and slope was positive the line belonged to right
4. For both the sets of left and right lines, the average of slope and intercepts is calculated and left and right lanes are drawn.


### 2. Identify potential shortcomings with your current pipeline
1. The current algorithm is not robust to detect on different road surfaces
2. Just averaging the slopes and intercepts to decide the line is not a great technique. This can be improved further using sophisticated methods.



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to implement algorithm to detect lanes when the lane markings are curved. Currently the lane detection does not do a great job with road curvature. This can be improved further.
