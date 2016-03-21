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
- Environmental objects may be hard recognize
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
- switchable mode between explore to build/update map of new/unknown locations and navigate through a known map

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
- Multiple E-Stop access: on-board, remote, and software interfaces

# Vibration Compensator Options

- IMU
- IMU + Vision (RGB, global shutter camera)
- Vision only (Semi-Dense)
- Stereo camera (Feature-based from RGB space, followed by ICP in 3d space)
- LIDAR (exploit Local smoothness feature)
- Combine with smoothing and filtering methods to improve robustness and accuracy (global feature, and outlier rejection)

# Improvement Options for Robustness to initial pose
- Defer online localization, allow it to stabilize
- Use safe zoning to reject any spurious initial condition and also to reject invalid pairing in ICP
- Use feature based matching, such as FLIRT feature in 2D, or incorporate height/layer information as distance metric in ICP
- Use point to line or point to plane metric in ICP for more robust alignment
- Use additional smoothing or filtering at post-processing stage, but this must be done carefully as ICP itself needs a good initial values from previous cycle in order to converge correctly

# Note for Integration to Path planning and Control

- ICP based technique uses a Delayed Estimation approach, i.e. the pose correction is delayed until local map is built from accumulated laser scans over ceretain short distance. It is possible, due to high error , large correction to be made. Thus for safe control, a smoothing layer can be added at post processing stage
- Of course, too large correction may not be an accurate estimation, but this is handled by improving robustness of the localization itself, (see previous slide)

# Possible directions

\begin{enumerate}
\item{Map-based object detection as prior to machine learning based object detection (points, and its local surface normal, and its relation to other points in an object representation)}
\item{Object level SLAM instead of point clouds}
	\begin{enumerate}
	\item{Local fast, raw point cloud scan matching, for immediate control , and accumulator}
	\item{Voting system to detect object from accumulated point cloud from a  (learned) object model template}
	\end{enumerate}
\end{enumerate}

# Work Diagram

\resizebox{1.02\textwidth}{!}{
\begin{tikzpicture}[node distance = 1.2cm, thick, nodes = {align = center},
    >=latex]
  \node[Minimum Width = loop, shape = ellipse, fill = red] (imp-sol)
    {ellipsoid box};
  \node[Minimum Width = loop, fill = yellow, below = of imp-sol] (rec-box)
    {rectangular box, and very wiiiiiiiiiiiiiiide\\2nd line};
  \node[shift = (left:.5*x_node_dist)] at
    ($(imp-sol.west|-imp-sol.south)!.5!(rec-box.north west)$) (for-1)
    {formula 1};
  \node[shift = (right:.5*x_node_dist)] at
    ($(imp-sol.east|-imp-sol.south)!.5!(rec-box.north east)$) (for-2)
    {formula 2};
  \begin{scope}[on background layer]
    \node[fit = (for-1)(for-2)(imp-sol)(rec-box), basic box = blue,
      header = DMFT loop] (dmft-l) {};
  \end{scope}
  \path[very thick, blue, hv] (rec-box) edge[->] (for-1) edge[<-] (for-2)
                              (imp-sol) edge[->] (for-2) edge[<-] (for-1);

  \node[east above = of dmft-l, basic box = green, header = DMFT prelude]
    (dmft-p) {Math and text math and text math and text\\
              math and text math and text math and text};
  \node[north left = of dmft-l, basic box = green, header = $\rho$ update,
     shift = (down:y_node_dist)] (rho)
    {Much more text much more text\\much more text much more text};
  \node[basic box = blue, header = DFT part, anchor = north] at
    (dmft-p.north-|rho) (dft) {So much text so much text so much text\\
    I think I need \texttt{tikz-lipsum}\\or something like that.};
  \node[basic box = green, anchor = north] at
    ($(dft.north east)!.5!(dmft-p.north west)$) (upd) {update\\$math$};
  \path[fat blue line, <-, dashed, vh] (rho) edge
    ({$(rho.south)!.5!(dmft-l.south)$}-|dmft-l.south west);
  \path[fat blue line, ->]
    ({$(upd.south)!.5!(dmft-p.south)$}-|dmft-p.south west)
    coordinate (@) edge[<-, solid] coordinate[pos=.15] (@s)
    coordinate[pos=.9] (@e) (@-|dft.east)
    {[every edge/.append style=dashed, vh] (@s) edge[<-] (upd) (@e) edge (upd)}
    (h-rho) edge[dashed] (dft)
    ($(dmft-p.south)!.5!(dmft-p.south east)$)
    coordinate (@) edge (@|-dmft-l.north);
\end{tikzpicture}
}

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

- Robust Localization and Navigation framework
- Lidar Stabilization method
- Map building, teach and repeat case
- Map-less obstacle avoidance and path following/planning

# Software Package Description

\begin{table}[!t]
\renewcommand{\arraystretch}{1.3}

\label{table_cost}
\centering
\tiny
\scalebox{.65}{
	\begin{tabular}{p{2.3cm}||p{2.0cm}||p{8cm}||p{2.5cm}}
	\hline
		\textbf{Package} &
		\textbf{Input} & \textbf{Processes Description} & \textbf{Output} \cr
		\hline\hline
		\multirow{2}{*}{\parbox[t]{2.3cm}{Vibration\\Compensator}} & Image & Extract Image Feature from an Image & Image Feature \\\cline{2-4}
		& Image Feature \newline IMU & KLT Tracker: Real-time matching and alignment from frame-to-frame & Angular Pose \\
		\hline
		\multirow{4}{*}{Graph SLAM} & 3D/2D Laser Scans & Iterated Closest Point (ICP) & Laser Odometry \\\cline{2-4}
		& Laser Odometry \newline 3D/2D Laser Scans & Accumulate Laser Scans and build local map & Local Map \\\cline{2-4}
		& Local Map \newline Global Map & Multiscans ICP, load portions of global map, local-to-local map ICP & Global Robot Pose \newline Global Map\\\cline{2-4}
		& Local Map \newline Global Map & Loop Closure Detection and Graph Optimization & (optimized) Global Map\\
		\hline
		3D Object Detection & 3D Laser Scans \newline RGBD \newline Local Map (from Localization) & Ground removal, Clustering point cloud, improved accuracy from local map & Obstacle Poses   \cr
		\hline
		2D Local Map & Robot Pose\newline Global Map\newline 3D Laser Scan\newline 2D Laser Scan & Surrounding sliding window local map super imposed with obstacles data. Project into 2d plane for easy navigational reference, elevation information is available if 3D laser scan is in the input. Elevation is useful for leg placement. & 2D Local Grid Map \newline 2D Local Elevation Map\cr
		\hline
		People Tracker & Leg Pose\newline Person Pose & Two level Kalman Filter-based People Tracking & Tracked People Pose\cr
		\hline
		\end{tabular}
}
\end{table}


# Timeline

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
\begin{gantt}[xunitlength=0.9cm,fontsize=\small,titlefontsize=\small,drawledgerline=true]{10}{18}
-->
[\\]: <> (\tikzset{every picture/.style={yscale=0.3,transform shape}})
\begin{figure}[htb]
\centering{\resizebox{1.02\textwidth}{!}{
  \begin{gantt}[xunitlength=0.9cm,drawledgerline=true]{11}{18}
    \begin{ganttitle}
    \titleelement{2016}{9}
    \titleelement{2017}{9}
    \end{ganttitle}
    \begin{ganttitle}
    \numtitle{4}{1}{12}{1}
    \numtitle{1}{1}{9}{1}
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
  \end{gantt}}
  }
\end{figure}
