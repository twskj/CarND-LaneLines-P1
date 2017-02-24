#**Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

My pipeline consisted of 5 steps. 
 1. Converteing the images to grayscale
 2. Smoothing the edge using Gaussian blur
 3. Putting image to Canny algorithm to detect edges.
 4. Masking out using triangular shape
 5. Detecting lines using Hough Transform algorithm
 6. Averaging slope and intercept for left and right lane line
 8. Merging result to the original image
 9. Write result


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by finding slope and intercept of each line. I then weighted average (based on length of each line).

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there's no line is detected.
Another shortcoming could be when area of interest are not in the assumption space i.e. different mounting position of a camera.


###3. Suggest possible improvements to your pipeline

A possible improvement would be to enlarge area of edges. More lines means potential information.
But also need to tune line detection parameter so that I don't get all the noises.

Another potential improvement could be to use
