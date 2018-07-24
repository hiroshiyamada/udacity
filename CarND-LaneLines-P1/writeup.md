# **Finding Lane Lines on the Road** 

## Hiroshi Yamada

### I use this template file for my writeup. I want to submit it as a markdown file. 
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight.jpg "result1"
[image2]: ./test_images_output/solidYellowCurve2.jpg "result2"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. I mostly did the same procedures as the instructions of this project. First, I converted the images to grayscale. Second, I use gausssian filters for the grayscaled image. Third, I detect edges by using canny functions. Fourth, I masked images using polyfit funtions. Fifth, I used hough transformations and detect lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function.
I detect whether lines are left or right by using the slope of lines. Then, I gathered slope values of each left and right lines, and use the median of slopes as a left and right slope. I also decide the one point of left and right line in addition to decide slope.  I gathered lower points of [x1, y1] or [x2, y2] and use medians of points the same way as I did for the slope.

Result of sample images are below: 

![solidWhiteRight][image1]
![solidYellowCurve2][image2]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road is curving.
Currently, my program only detects straight lines.

Another shortcoming could be what would happen when it is dark.
My paramters are constants, so I guess my program cannot detect white lanes in a dark scene.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a spline for the curvature.

Another potential improvement could be make the parameters variables.
I need to find optimized variables for each different scenes.