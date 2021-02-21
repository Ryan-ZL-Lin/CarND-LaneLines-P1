# **Finding Lane Lines on the Road** 

## Writeup Report

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1.Pipeline Description

* My pipeline consisted of 6 steps. 

1. I converted the images to grayscale.
2. I assigned 13 to the kernal size for Gaussian smoothing and got a lur image
3. I assigned 30 and 150 to the low and high threshold for Canny edge detection.
4. I defined an ROI (region of interest) in the image and add the edges detected from step 3.
5. I defined the parameters of Hough transform and draw the lings on the image directly.
6. I merged the origina limage and the lines derivied from step 5 into one single output image.

---

* In order to draw a single line on the left and right lanes, I modified the draw_lines() function by following steps: 

1. Loop through all the lines and separate them into array left_slopes and right_slopes to represent the lines from left and right land marks.
2. To filter the potential horizontal lines, the slope (absolue value ) under 0.2 wont be included.
3. Calculate the average in left_slopes and right_slopes.
4. Calculate the coefficients of lift and right land marks based on the average slopes and the coordinates defined in ROI.
5. Calculate the final coordinates of the lift and right land marks based on the result from step 3 and step 4.
6. Draw 2 lines in the image based on the reuslt from step 5.


If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
