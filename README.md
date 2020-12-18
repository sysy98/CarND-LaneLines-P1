# **Finding Lane Lines on the Road**

The goals this project is **find lane lines on the road**.
---

### 1. Pipeline.

My pipeline consisted of 5 steps.
* First, I converted the images to **grayscale** and used **gassian blur** to get smoother derivatives of image.
* Second, I used **Canny** detection and set high and low threshold to get edges.
* Then, I used a **region mask** to limit the detection area.
* Since theses edges are consist of points, I have to use **Hough transfrom** to find lane lines.
* At last, I combine line image with original image by using **Weighted image**.
---
In order to draw a single line on the left and right lanes, I modified the draw_lines() function:
* Distinguish the left and right lane lines by the slope of the straight line, while excluding infinite slope values.
* Calculate the average of the four coordinates of the left and right lanes.
* Used **Polyfit()** calculate slope and offset of lines respectively. And then I can get start and end points of each line.
  Then connect start and end points.


### 2. Shortcomings with my current pipeline

When the video frame changes, the detected lane line will shake.


### 3. Possible improvements to my pipeline

* Use **cv2.inRange()** to select lanes first by setting GRB or HSV criterion.
  Set a mask to identify the yellow and white lines on the road.
  And use **cv2.bitwise_and(img, img, mask)** get selected image.
