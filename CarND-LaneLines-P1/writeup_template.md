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

My pipeline consisted of 5 steps. 
First, I converted the images to grayscale, 
then I use gaussian blur the grayscale image,
then I use canny to extrace the edges,
then I use region of interest to draw the mask,
then I use hough lines to extrace all the lines in the region,
then I use angles to seperate right lines and left lines : (30 ~ 60) for the right side; (-30 to -60) for the left side,

(following steps repeat twice for the left side and right side)
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
I calculate the centroid point of each line
then I choose the median one from all the centroids,
then I calculate all the slopes of all the lines,
then I choose the mean slope of all the slopes,
then from the median point and the slope, I draw a line within the top and bottom area of the region of intreasts. 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

Please check the P1 ipython notebook to see the test image results. Thanks!


### 2. Identify potential shortcomings with your current pipeline


I haven't got enough time to tidy up the code. 
For choosing the centroid point and slope once, sometime the line is not consistent with previous frame. 


### 3. Suggest possible improvements to your pipeline

To solve the inconsistency issue, I need to do time series smoothing to normalise the centroid point and also the slope. 
