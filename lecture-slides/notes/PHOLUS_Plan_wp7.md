[\\]: <> (\usepackage{outlines})
<!--
% Plan on WP 7 (PHOLUS)
% Saputra V.B.
% Mar 14, 2016
-->

---
title: Plan on WP 7 (PHOLUS)
author: Saputra V.B.
date: Mar 14, 2016
---
# Overview

- Problem Description
- Challenges
- Proposed Method and Strategy
- Safety Barrier
- Work Diagram, Hardware List and Expected Timeline

# Problem Description

- Self localize in unknown indoor and outdoor environment without the help of GNSS
- Plan and perform point A to B navigation in both known and unknown environment
- Travel up to 6km/h (~2m/s) for flat road and up to 2 km/h (~.7m/s) for outdoor unstructured terrain
- Platforms level of autonomy shall be dynamically varied based on resource or task constraints
- Allow human intervention at anytime
- Able to move in narrow passage way
- Leverage or use environmental objects to aid stabilize itself in navigation or accomplishing task

# Challenges

- High frequency motion can disturb LIDAR localization
- Outdoor unstructured terrain may contain difficult features
- The Quadruped robot may sway during navigation
- Many data set are required to test algorithm

# Strategic Approaches
<!--
* yes  
  * oh yesss
\begin{figure}
\includegraphics{GearControl-cropped.pdf}
\end{figure}
- ah shit
2d Elevation map
switchable mode for navigation, exploration, 
\begin{outline}
\1 First level
\1 First level again 
\2 Second level again
\3 Third level 
\3 Third level agaim
\end{outline}
Note that the 4th level is not allowed in Beamer
\begin{outline}[enumerate]
\1 First level
\2 Second level 
\1 First level again 
\2 Second level again
\3 Third level 
\3 Third level agaim
\0 Some normal text whitin outline environment. \par
\1 Another list
\end{outline}
-->

## Localization

- explore, build map, navigate to same place (full SLAM)
- given prior map, bootstrap robot location, localize and navigate (online SLAM)
- switchable mode between explore to build map of unknown locations and navigate through a known map

## Support Structure for Localization
- Tree-based (hierarchical) map representation for global localization
- Loop closure based on features extracted from LIDAR and/or images
- Use probabilistic approach to determine confidence of robot position
- Make certain local navigation decision to quickly prevent lost and relocalize

# Strategic Approaches (2)

## Obstacle Detection and Local Map
- Simple height threshold or ring-to-ring distance
- Clustering and segmentation with bounding box/circle
- Ground surface detection and accumulation
- Object classification (?)

## Support structure for Obstacle Local Map
- Local 2D elevation grid map
- Potential field based local 3D motion planning, and obstacle avoidance
- Compute affordability based on the local map (and other parameters)

# Safety Barrier
- Fiber optic IMU
- High rate global shutter camera
- 3D stereo camera and LIDAR for localization
- UWB system for preventing robot total lost for safety reasons
- Cover robot with collision safe material

# Vibration Compensator Options

- IMU
- IMU + Vision (RGB, global shutter camera)
- Vision only (Semi-Dense)
- Stereo camera (Feature-based from RGB space, followed by ICP in 3d space)
- LIDAR (exploit Local smoothness feature)
- Combine with smoothing and filtering methods to improve robustness and accuracy (global feature, and outlier rejection)

# Work Diagram


# Hardware List 

## Sensors
- Structure IO camera
- ZED Stereo Camera
- Velodyne 16/32 outdoor LIDAR
- High sample rate Global Shutter camera
- IMU(s) 

## Computing Devices
- Compact PC with i7 Intel processor, 8 GB RAM min.
- Odroid XU4 
- NVIDIA Jetson TK1

# Expected Outcome



## Deliverables

## Timeline

<!--
\begin{ganttchart}{12}
\gantttitle{2011}{12} \\
\gantttitlelist{1,...,12}{1} \\
\ganttgroup{Group 1}{1}{7} \\
\ganttbar{Task 1}{1}{2} \\
\ganttlinkedbar{Task 2}{3}{7} \ganttnewline
\ganttmilestone{Milestone}{7} \ganttnewline
\ganttbar{Final Task}{8}{12}
\ganttlink{elem2}{elem3}
\ganttlink{elem3}{elem4}
\end{ganttchart}
-->
\begin{figure}
  \begin{gantt}{10}{12}
    \begin{ganttitle}
    \numtitle{1}{1}{12}{1}
    \end{ganttitle}
    \ganttbar{a task}{0}{2}
    \ganttbarcon{a consecutive task}{2}{4}
    \ganttbarcon{another consecutive task}{8}{2}
    \ganttmilestone[color=cyan]{Milestone with color!}{4}
    \ganttbar{another task}{2}{2}
    \ganttbar[color=cyan]{another coloured task}{4}{4}
    \ganttbar{another task}{4}{2}
    \ganttcon{4}{5}{4}{7}
    \ganttmilestonecon{A connected Milestone}{7}
    \ganttbarcon{another consecutive task}{8}{2}
  \end{gantt}
\end{figure}
