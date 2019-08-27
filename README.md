## Finding Lane Lines on the Road


[//]: # (Image References)

[image1]: ./report_images/original.jpg "Original"
[image2]: ./report_images/gray.jpg "Grayscale"
[image3]: ./report_images/smoothed.jpg "Smoothed"
[image4]: ./report_images/cannyEdge.jpg "CannyEdge"
[image5]: ./report_images/lines.jpg "Lines"


### 1. Pipeline description. As part of the description, and how the draw_lines() function was modified.

My pipeline consisted of 5 steps. 
1) I converted the images to grayscale. 
2) I smoothed the images by applying guassian filter. 
3) Applied Canny edge finding to get the edge/gradient information. 
4) Used a four sided polygon mask to keep the region of interest. 
5) Applied Hough transform to find the left and right lane lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
1) Decided left or right lane lines by using slope i.e. slope = (y2-y1)/(x2-x1). It is considerd as left line if slope < 0. It is considered right line if slope > 0.
2) Used polyfit to find the target line for left line and right line respectively.
3) Calculated the corresponding x based on the boundary y value in order to extrapolate the line.

The images for each step are shown as below: 

![Original Image][image1]
![Gray Image][image2]
![Smoothed Image][image3]
![Canny Edge Image][image4]
![Lane Line Image][image5]


### 2. Potential shortcomings with current pipeline


One potential shortcoming would be what would happen when image quality is not good, for example, bad lighting/brightness. It may be difficult to find the lane lines.

Another shortcoming could be the "draw_lines()" function is very simple/naive. It may not work well when Hough transform result is bad.


### 3. Suggestion for possible improvements to the pipeline

A possible improvement would be to apply some pre-image processing methods to enhance image quality.

Another potential improvement could be to try the modified Hough tranform or try a higher degree poly fitting (rather than one degree).
