# udacity
Self Driving Car Nano Degree Projects
# **Finding Lane Lines on the Road** 



---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road from the given images
* Detect lane lines in the video clips provided by udacity
* Reflect on your work in a written report


### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of following steps. First, 
1. I converted the images to grayscale
2. Defined my boundary of interst in the image
3. Get the canny image after applying gaussian blur
4. Using hough lines method, I got coordinates of all the lines detected
5. I wrote one new function two_lines which will takes input as lines coordinates detetcted by hough lines function and check if it's left line or right line.
6. After getting all the left lines and right lines, I extrapolated all the line to the upper and lower boundary. I ignored the lines which ends are out of boundary. I took median of all the left line and right lines separately so that I have only one extrapolated left line and one extrapolated right line. After I drew the line in red with thickness 12 and imposed it on original picture.
Please check the Create_PipeLine_from_Image.ipynb for the actual program and output

### 2. Detecting Lanes on video
I used the same method on video to draw the lines on video clips images. It worked fine for solidWhiteRight.mp4 and solidYellowLeft.mp4 but did not work for challenge.mp4 because the images had too many detected false lines because of shadows and brightness. 
Using my pipeline method many frames did not detect any right line in the lane, all the right lines were noise so program ignored it. 
To avoid this problem I stored median data for last good image and if I don't get lanes detected on either side I will use coordinates of last stored line to drar line on that side. It worked well for challenge.mp4 video. 


### 3. Identify potential shortcomings with your current pipeline


As per my analysis the noise removal method I am using is not elegent solution and I believe noise can be removed by differentiating shadow/brightness from actual white/yellow line

### 4. Suggest possible improvements to your pipeline

A possible improvement would be to detect the noise line data in better and full proof way.
