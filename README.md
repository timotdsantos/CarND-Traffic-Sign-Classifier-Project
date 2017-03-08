#**Finding Lane Lines on the Road** 

---

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on the work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./examples/canny.jpg "Canny"
[image3]: ./examples/poly_mask.jpg "Polygon Mask"
[image4]: ./examples/LR_lines.jpg "Left and Right Lines"
[image5]: ./examples/mismatch_top.jpg "Overlap"
[image6]: ./examples/match.jpg "Matched"
[image7]: ./examples/match_red.jpg "Final Image"

---

###1. Describe the pipeline. As part of the description, explain how you modified the draw_lines() function.

The pipeline consisted of three sections:
- line detection
- line aggregation
- line extrapolation

 **The Line Detection** results in multiple lines detected within the area of interest. 
 It consists of the following processing steps
    1 Convert to grayscale

![alt text][image1]    
    2 Gaussian smoothing - kernel size was determined iteratively to avoid noisy output
    3 Canny edge detection  - thresholds were also iteratively selected

![alt text][image2]    
    4 Applying polygon mask - a trapezoid was chosen as the area of interest
    
![alt text][image3]    
    5 Hough transform - thresholds were also iteratively selected to minimize false positives

**The line aggregation** could be found in the modified draw_lines function.
It consists of filtering out the irrelevant detected lines and consolidating them to the left lane or right lane. 
Here are the processing steps taken:

   1 Horizontal Lines were discarded
   2 Slope of detected lines were calculated and discarded if absolute value is below a certain threshold. 
       I used the slope_threshold=1, which retains the lines steeper than the 45-degree angle.       
   3 Negative and Positive slopes were seggregated.
   
![alt text][image4]   

   4 Left lines that are crossing over to the right half of the screen and right lines crossing over the left half are discarded  
   5 Line-fitting algorithm (polyfit) was used to generate 1 line for each side using the line edpoints as input


**The Line Extrapolation** consists of defining the coordinates to draw the line segments extending to the 
bottom edge of the screen, and matching length of the lanes.
   1 Get the points where the derived lane lines intersect with the bottom edge. I just used the polyfit linear equation.
   
   2 Matched the top endpoints of left and right lanes. I chose the point closer to the bottom, and got the corresponding 
      coordinate from the left and right fitted line.

![alt text][image5]

   3 Used the 4 points as input to draw the 2 lane lines on the image.

![alt text][image6]

###2. Identify potential shortcomings with your current pipeline


The algorithm would likely fail when there are lines at the middle of the road within the polygon Mask. 
Another case would be where the lines detected do not fall within the thresholds that I have set, or when there are large patches of missing lines. 
A road that's not plain, having different shades, shadow, or color patches may be troublesome. 

###3. Suggest possible improvements to your pipeline

A possible improvement would be to create a different or adaptive mask.
I could also look at smoothing across different frames/images.
A way to classify false positives would be a good additional step to make the solution robust.

