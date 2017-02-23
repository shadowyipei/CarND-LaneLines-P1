#**Finding Lane Lines on the Road** 

### Pipeline Details

Current pipeline consists of 6 steps:

 1) Transfer image from RGB to HSV, and utilize channel V instead of grayscale as in example.
 
 2) Process Gaussian blur on the transferred image.
 
 3) Process Canny edge detection.
 
 4) Create a region of interest and only keep edges in this region.
 
 5) Process Hough Transform 
 
 6) Draw lines
    - Categorize lines into two sets: left lines & right lines.
    - Filter out noise lines by checking on line slope and the coordinate of (x, img.shape[0])
    - Calculate average of left line slopes and average of (x, img.shape[0]) on left lines as left lane's k and b in y = kx + b
    - Calculate average of right line slopes and average of (x, img.shape[0]) on right lines as right lane's k and b in y = kx + b
    - Draw the left lane and right lane.

### Potential shortcomings

There are several shortcomings in this pipeline

 1) The whole pipeline is optimized based on the comera postion on the car and it can not detect street corners like
    ---------------------

    --------     --------
           |     |
           | car |
           
 2) Another potential issue is when the car passes through a intersection when there are no line marks on the road, this pipeline can't detect the lanes.
 
 3) There are still arrcuracy issues on finding lanes and filtering out noise lines: In the challenge video, the left lane bounces out of the actual yellow lane in some image frames. 

###3. Suggest possible improvements to your pipeline

 1) To improve the accuracy, some parameters could still be tuned.
 
 2) In order to reduce noise lines when calucats left lane and right lane, other mechanim needs to be deployed to filter out lines which are far off the caculated lanes.   
