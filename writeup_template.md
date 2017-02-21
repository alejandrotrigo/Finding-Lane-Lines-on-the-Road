#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/gray.png "Grayscale"
[image2]: ./examples/canny.png "Canny edge"
[image3]: ./examples/region.png "Region of interest"
[image4]: ./examples/hough.png "Hough Transformation"
[image5]: ./examples/final.png "Final image"


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale ![alt text][image1], then I apply a smoother Gaussian filter to make easyer the Canny edge dection with a kernel = 5 (just try and error). After that I apply Canny edge detection ![alt text][image2] with the threshoslds in a proportion of 1/3 (50-150), then I select the region of interest ![alt text][image3], also a little bit of try and error with the vertices, and apply the Hough transformation. ![alt text][image4] I had to change many times the attributes because of my draw_lines() function (sometimes the gap between connectable line segments was bigger in the practice so the function was failing because of empty arrays)

In the draw lines function I followed your indication and worked with the slope, and basic functions of numpy array, such as polyfit and poly1d for dealing with negative values, fitting the points into the line and drawing it. Finally I drawed the line using the coordinates of the points of the array.

Finally I used the weighted_img function to get again the initial image with the lanes.
![alt text][image5]

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when we are working in a curve road.

Another shortcoming could be the dark shapes. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to change the draw_lines() function again and the parameters of the hough transformation to let the pipeline deal with curved roads.