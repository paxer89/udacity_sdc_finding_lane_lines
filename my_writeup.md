# **Finding Lane Lines on the Road** 

## Writeup Pascal 02/28/2020

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---
You can find my code in "my_P1"

---

### Reflection

### 1. Pipeline description

My pipeline consisted of 8 steps.

1) I converted the images to grayscale

2) I apllied gaussian blur, kernel_size 3 as used in the lessons 

3) I extracted canny edges

4) I applied a region of interest relatively to the image.shape

5) I searched for hough lines in the edges

6) I modified the draw_lines() function
    - iterate through all the line segments
       
    - calculate slope and offset parameter for eacht segment
            m=(y2-y1)/(x2-x1)
            b=y1-m*x1
            
    - seperate in left line m<0 and right line m>0
    
    - store slope and offset in seperate lists for left and right if they're above a certain threshold
    
    - calculate average line parameters for left an right line
    
    - calculate start and end point of left an right line with averaged parameters within the ROI
    
    - drawing left and right line

7) I overlayed the lines with the original image

8) I apllied the above the every single frame of the videos



### 2. Identify potential shortcomings with your current pipeline


Shortcomings would be:
   
   - the lines are flickering a bit too much
   
   - apllying the pipeline to curvy roads, because only straight lines are drawn
   
   - a differently mounted camera would not meet the fixed ROI
   


### 3. Suggest possible improvements to your pipeline

Possible improvements would be:
    
   - somehow organize better my threshold for the slopes,  sometimes i get NaN errors
   
   - filtering the lines with previous images to minimalize flickering
   
   - approximate the lane lines with clothoids or s.th. instead of straight lines to fit better curved roads

