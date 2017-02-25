#**Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

My pipeline consisted of 8 steps. 
 1. Converteing the images to grayscale
 2. Smoothing the edge using Gaussian blur
 3. Putting the image to Canny algorithm to detect edges.
 4. Masking out using triangular shape where the tip is in the middle of the screen and the base are to bottom of the screen
 5. Detecting lines using Hough Transform algorithm
 6. Filtering and averaging lines to get two final lines-- left and right lane mark
 8. Merging result to the original image

In order to draw a single line on the left and right lanes, I start from filtering out noise (lines that are not lane line using a few pre-define conditions. I then average the valid lines to get the result lines. The result line will be add to history and average over 10 frames to get the final lines.

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline

One potential shortcoming is that my algorithm prefer to have more lines in the image from pre-processing.
That will likely cause more noise in real situation.

Another shortcoming is that the filtering process make assumption that the camera will always on the center of the screen. which may or may not be true.

Lastly, the algorithm doesn't really have a concept of a "lane". It only detect lines and therefore easily confuse with outlier and other noices.

###3. Suggest possible improvements to your pipeline

A possible improvement would be to enlarge area of edges. More lines means potential information.
But also need to tune line detection parameter so that I don't get all the noises.

To improve, all hard coding parameter need to be dynamic. Currently, a certain set of parameter is good for a bright and high contrast background but fail to detect lines when the lightning condition change such as going into a tunne shades from building and tree. It would be great if parameter is tune on the fly according to the environment instead of hand picking at compile time/coding time.
