# **Finding Lane Lines on the Road** 

## Writeup Report

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"
[image2]: ./test_images_output/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"
[image3]: ./test_images_output/solidWhiteRight.jpg "solidWhiteRight"
[image4]: ./test_images_output/solidYellowCurve.jpg "solidYellowCurve"
[image5]: ./test_images_output/solidYellowCurve2.jpg "solidYellowCurve2"
[image6]: ./test_images_output/solidYellowLeft.jpg "solidYellowLeft"
[image7]: ./test_images_output/hLine2.jpg "hLine2"
[image8]: ./test_images_output/hLine3.jpg "hLine3"

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


* In order to draw a single line on the left and right lanes, I modified the draw_lines() function by following steps: 

1. Loop through all the lines and separate them into array left_slopes and right_slopes to represent the lines from left and right land marks.
2. To filter the potential horizontal lines, the slope (absolue value ) under 0.2 wont be included.
3. Calculate the average in left_slopes and right_slopes.
4. Calculate the coefficients of lift and right land marks based on the average slopes and the coordinates defined in ROI.
5. Calculate the final coordinates of the lift and right land marks based on the result from step 3 and step 4.
6. Draw 2 lines in the image based on the reuslt from step 5.


Here are some images to show how the pipeline works

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]
![alt text][image7]
![alt text][image8]

---

### 2. Identify potential shortcomings with current pipeline

* One potential shortcoming would be what would happen when the car ahead is at the middle of the image. 

* Another shortcoming could be that the lines produced by the pipeline are not able to be curve.

---

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to remove the car's edge in the image to detect the land mark more accurately.

Another potential improvement could be to have a function to draw a curve lines in the image to represent the real land marks.
