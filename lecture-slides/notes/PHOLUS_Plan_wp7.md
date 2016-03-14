[\\]: <> (\usepackage{outlines})

---
title: Plan on WP 7 (PHOLUS)
author: Saputra V.B.
date: Mar 14, 2016
---
<!--
% Plan on WP 7 (PHOLUS)
% Saputra V.B.
% Mar 14, 2016
-->

# Overview

- Problem Description
- Challenges
- Proposed Method and Strategy
- Safety Barrier
- Work Diagram, Hardware List and Expected Timeline

# Strategical Approaches
<!--
* yes  
  * oh yesss
\begin{figure}
\includegraphics{GearControl-cropped.pdf}
\end{figure}
- ah shit
2d Elevation map
switchable mode for navigation, exploration, 
-->

- explore, build map, navigate to same place (full SLAM)
- given prior map, bootstrap robot location, localize and navigate (online SLAM)
- switchable mode between explore to build map of unknown locations and navigate through a known map
 Methodology
- Tree-based (hierarchical) map representation
- Loop closure based on features extracted from LIDAR and/or images
- Use probabilistic approach to determine confidence of robot position
- Behavior module to decide between modes, and possibly make certain local navigation to increase confidence and relocalize

# Vibration Compensator Options

- IMU
- IMU + Vision (RGB, global shutter camera)
- Vision only (Semi-Dense)
- Stereo camera (Feature-based from RGB space, followed by ICP in 3d space)
- LIDAR (exploit Local smoothness feature)
- Combine with smoothing and filtering methods to improve robustness and accuracy (global feature, and outlier rejection)

