---
title: "Graduation Project: Vision System For Self Driving Cars"
layout: post
date: 2017-10-30 6:46
#tag: jekyll
image: https://www.youtube.com/watch?v=XMmFEx03v1E
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "My Bachelor Thesis at Alexandria university"
category: project
author: Mostafa
externalLink: false
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/XMmFEx03v1E" frameborder="0" allowfullscreen></iframe>

The project goal was to achieve many vision tasks for self-driving cars using multiple cameras and a lidar in real-time.  This Project was part of [Autonomous Electric Vehicle](http://ihub.asu.edu.eg/igp2016-2017.html).

---

#### Project features:

- Depth Computation using stereo vision.
- Free Space and Obstacle Detection.
- Lane Detection.
- Car and Pedestrian detection.
- Object Tracking.
- SLAM.

#### My Role:

* **Depth Computation[[Github]](https://github.com/misaleh/libelas-gpu):**

Our objective was to cover the 360 view around the car. For the main front view we used [ZED camera](https://www.stereolabs.com/zed/specs/), and for the remaining view we would implement our system using Off-the-shelf hardware and the we would implement stereo algorithm to compute the depth and finally merge these depth maps into one 360 depth map using image stitching.

Regarding the ZED camera, getting depth information was easy as it provides APIs to interface with it.

Regarding the Stereo Algorithm, first I reviewed different local, global and Semi-global algorithms, evaluated and benchmarked them and also compared the output with the ZED output. 

Then I Implemented Part of ELAS algorithm on GPU using CUDA to enhance its performance on our platform [Jetson TK1](http://www.nvidia.com/object/jetson-tk1-embedded-dev-kit.html), ported x86 dependent code(SSE) to Jetson(ARM) and made more code optimization to achieve real-time depth map generation.

 Then worked in post processing of the generated depth map. Finally computed the pointcloud from the depth map as it is used by other software modules.

* **Free Space and Obstacle Detection[[Github]](https://github.com/misaleh/Free-space-and-obstacle-detection)**:

Implemented Free Space and Obstacle Detection algorithm using Occupancy Grids and  Dynamic Programming, based on this [paper](http://vision.jhu.edu/iccv2007-wdv/WDV07-badino.pdf).

Then Implemented Faster version using segmentation by thresholding without Dynamic programming.

And Finally Implemented a GPU version using CUDA which reached 38 fps.


* **Integration of Visual odometry with ROS framework:**

Integrated Visual odometry Code(C++) with ROS, by wrapping it with ROS APIs to create a package compatible with the software.

---