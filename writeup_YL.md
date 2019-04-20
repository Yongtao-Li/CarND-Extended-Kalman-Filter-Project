# **Extended Kalman Filters** 

## Yongtao Li

---

**Extended Kalman Filters Project**

The goals / steps of this project are the following:
* implement the extended Kalman filter in C++
* compile, build and run the code
* use a simulator to provide simulated lidar and radar measurements of a moving object
* cosim with Extended Kalman Filters and measure the performance

[//]: # (Image References)

[image1]: ./Docs/dataset1_Lidar_Radar.png "dataset1"
[image2]: ./Docs/dataset2_Lidar_Radar.png "dataset2"
[image3]: ./Docs/dataset1_Lidar_Radar_NoNorm.png "NoNorm"
[image4]: ./Docs/flowchart.png "flowchart"

## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/748/view) individually and describe how I addressed each point in my implementation.  

---

#### 1. Compiling

All the source code compile and run successfully on my local machine. Since I'm using Windows10, I chose to setup the environment to run Ubuntu Bash on Windows. I followed the steps in "Environment Setup (Windows)" section and it works pretty well!

#### 2. Accuracy

As you could see from the following two snapshots that my code works pretty well with both Dataset1 and Dataset2. My px, py, vx, and vy RMSE are less than or equal to the values [.11, .11, 0.52, 0.52].

| Dataset1 result   | Dataset2 result   |
|:-----------------:|:-----------------:|
|![alt text][image1]|![alt text][image2]|

#### 3. Follows the Correct Algorithm

I followed the exact flow chart in the previous lessons.

![alt text][image4]

Please see FusionEKF.cpp line 80-110 for how to use the first measurements to initialize the state vectors. Please see line 40-68 for initiate covariace matrix and measurement matrix.

In FusionEKF.cpp line 125-143, I made the prediction and then update state in line 155-171.

In the main.cpp line 130, the RMSE was calculated between estimations and ground truth.

One of the lessons learned is the importance of normalizing the angle when calculating measurement and state error. The following snapshot shows the result if not having this normalization. You could see that it was tracking pretty well until the object turned over 180 degrees and the estimation became way out of the measurement.

![alt text][image3]


#### 4. Code Efficiency

Overall the code is developed based on previous lessons, which are pretty concise and not having duplicated calculations or necessary flow controls.

