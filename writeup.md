# **Finding Lane Lines on the Road**

## Writeup Template

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./assets/solidWhiteRight-gray.jpg "Grayscale"
[image2]: ./assets/solidWhiteRight-blurgray.jpg "Blur gray"
[image3]: ./assets/solidWhiteRight-edges.jpg "Canny edge detection"
[image4]: ./assets/solidWhiteRight-region.jpg "Region of interest"
[image5]: ./assets/solidWhiteRight-result.jpg "Output"
[image6]: ./assets/shortcoming1.png "Shortcoming1"
[image7]: ./assets/shortcoming2.jpg "Shortcoming2"
[image8]: ./assets/shortcoming2-result.jpg "Shortcoming2 Output"
[image9]: ./assets/shortcoming2-edges.jpg "Shortcoming2 Canny edge detection"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I changed the images to grayscale, then I applied Gaussian blur to previous result. And I converted it to objects lines using by Canny edge detection. Next, I chose the region of interest on the converted image. Finally, I draw lines upon the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. First, I divided two section by its slope: positive or negative, then I divided sections by locations of x1 and x2. Because a few of lines made incorrect slope lines what I want. If the x1 and x2 located in incorrect side, I changed values to previous values. After that I calculated each average to make both side of a representative line.

If you'd like to include images to show how the pipeline works, here is how to include images:

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when something bright color of objects on the road. Please see the next image, and you can see that right line is slightly weird due to a short line on bottom right.

![alt text][image6]

Another shortcoming could occur when the brightness of road change suddenly. Looks like below, my algorithm did not cognize the lanes when the road changed asphalt to cement. As a result, edge detection lines drew border between asphalt and cement.

![alt text][image7]
![alt text][image8]

Last shortcoming would be unclear Canny edge detection. I tried to tune hyperparameters several times, I did not find suitable values for a clear shape.

![alt text][image9]

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to find proper values of parameters of Canny edge detection, also I could change an algorithm in draw_line() function for drawing more clear lines.

Another potential improvement could be to check out how to emphasis lanes, although hard conditions are showing in an image. Such as, ignoring the hood lines, judging something small and strange objects on the road, and setting up more suitable region of interest.
