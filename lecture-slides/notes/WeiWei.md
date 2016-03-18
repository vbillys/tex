---
title: Robot Building Project
author: Saputra V.B., Huang W., Chang T.W., Zhou L. B.
date: Mar 17, 2016
---

# Overview

- Robot Functionality
- Robot Overview Design
- Robot Components
- Budgeting
- Work plan


# Robot Functionality

- Can navigate in indoor environment
- Can detect simple objects (boxes) and pick up
- Can switch/touch certain simple panel
- Sound source direction detection
- Able to travel on small slope
- Maximum travel speed 2 m/s
- Expected operational hours, 4 hours
- Auto charge
- Can carry 1 kg object load
- Simple Interaction with people


# Robot Overview Design

## Robot Base
- Differential Drive
- Three wheeled, two driven, one caster
- Carry up to 50 kg load

## Robot Upper Body
- Fixed chest, with two 4-DOF arms
- One pitch DOF head, (servo) with vision sensor (RGBD)

# Robot Overview Design (2)

\begin{figure}
\includegraphics[scale=0.9]{robot_diagram.pdf}
\end{figure}


# Robot Components (Motors & Power Supply)

- Motors and Gearboxes
- Motor controllers 
- CANBUS Interface
- Battery
- Power Regulator
- Charging circuit for auto-charge



# Robot Components (Sensors)

- RGBD Sensor (structure.io / ZED camera / Kinect )
- 2d LIDAR (RP Lidar)
- 2 UWB Antennas

[\\]: <> (- Velodyne 16 (Next Proto!))
[\\]: <> (- Camera (high res, for outdoor!))

\begin{columns}
\column{0.33\textwidth}
\begin{figure}
\includegraphics[scale=0.2]{asus_xtion.jpg}
\end{figure}
\column{0.33\textwidth}
\begin{figure}
\includegraphics[scale=0.15]{zed_pic.pdf}
\end{figure}
\column{0.33\textwidth}
\begin{figure}
\includegraphics[scale=0.6]{zed_mechanical.pdf}
\end{figure}
\end{columns}


# Robot Components (Sensors) - RPLidar \& Decawave UWB Antennae

\begin{columns}
\column{0.5\textwidth}
\begin{figure}
\includegraphics[scale=0.3]{rplidar_pic.pdf}
\end{figure}
\column{0.5\textwidth}
\begin{figure}
\includegraphics[scale=0.35]{rplidar_mechanical.pdf}
\end{figure}
\end{columns}
\begin{figure}
\includegraphics[scale=0.7]{trek_pic.pdf}
\end{figure}


# Robot Components (Compute Devices)

## Intelligent PC(s)

- 2 Compact PC (Gigabyte/Shuttle PC) - one with GPU
- Standard LAN Router (Cisco)

## Motor PC(s) Modularized

- A9 for Base plus Watch Dog function
- Odroid x2 for two arms


\begin{columns}
\column{0.25\textwidth}
\begin{figure}
\includegraphics[scale=0.1]{odroid_pic.jpg}
\end{figure}
\column{0.75\textwidth}
\begin{figure}
\includegraphics[scale=0.45]{odroid_mechanical.png}
\end{figure}
\end{columns}

# Robot Components (Compute Devices) - GigaByte PC

Ultra compact PC design - 0.88L (59.6 x 128 x 115.4 mm)  
Require heat to flow out

\begin{figure}
\includegraphics[scale=0.2]{gigabyte_1.jpg}
\end{figure}
\begin{figure}
\includegraphics[scale=0.2]{gigabyte_2.jpg}
\end{figure}

# Robot Components (Compute Devices) - A9 Motor PC

\begin{figure}
\includegraphics[scale=0.35]{A9_pic.pdf}
\end{figure}
\begin{figure}
\includegraphics[scale=0.8]{A9_mechanical.pdf}
\end{figure}

# Robot  Design & Fabrication

- Cable may snaps (we need solution)
- Consolidate all the motor selections and send to Mr. Soo
- We need to go few rounds to revise design
- Auto charging need design
- Try to shift the wheel to the center of the base
- Decide on whether the cabling go inside links
- Check the Korean motor controller for small solution, especially for the 3rd and 4th DOF arm motor

# Design Summary (So Far...)


\begin{table}[!t]
\renewcommand{\arraystretch}{1.3}

\label{table_cost}
\centering
\footnotesize
\scalebox{.85}{
\begin{tabular}{p{3.5cm}||>{\RaggedLeft}p{6cm}}
\hline
\textbf{Item} &
\textbf{Parameters} \cr
\hline\hline
Robot Total height & $1.3m$ \cr
\hline
Robot width & $70$ - $80cm$ \cr
\hline
1st DOF Hand motor & $200W$ \cr
2nd DOF Hand motor & $150W$ \cr
3rd DOF Hand motor & $40W$ \cr
4th DOF Hand motor & $40W$ \cr
\hline
Head motor & Dynamixel Servo \cr
\hline
Waist motor & $200W$ \cr
\hline
Base motor & Brushed Motors \cr
\hline
Auto-Charging System & Allow flexibility in navigation error ~5cm \cr
\hline
\end{tabular}
}
\end{table}

# Equipment Budgeting

[\\]: <> (\resizebox{width=4cm}{!}{)
[\\]: <> (\caption{Total cost excluding Fabrication and Design})
[\\]: <> (\sout{Camera (Point Grey)} & \sout{\$5000} \cr)

\begin{table}[!t]
\renewcommand{\arraystretch}{1.3}

\label{table_cost}
\centering
\footnotesize
\scalebox{.85}{
\begin{tabular}{p{6.cm}||>{\RaggedLeft}p{1.5cm}}
\hline
\textbf{Item} &
\textbf{Cost} \cr
\hline\hline
Compute Devices (2Gigabyte), Odroid, A9 & \$4000 \cr
Industrial Router and Industrial USB Hub & \$1000 \cr
\hline
RGBD Vision Sensor & \$2000 \cr
2d LIDAR (RP Lidar) x2 & \$1000 \cr
UWB Localization System & \$2000 \cr
\hline
Motors & ? \cr
Motor Drivers & ? \cr
CANBUS Interface & \$1000 \cr
Battery & \$6000 \cr
Power Regulator & ? \cr
\hline
Design & ? \cr
Fabrication & ? \cr
\hline\hline
Total & \$16000
\end{tabular}
}
\end{table}


# Work plan

- WeiWei : Overall Management, Robot UWB Localization, Manipulation
- TaiWen : Electrical
- Soo : Mechanical
- Billy : Navigation, Obstacle detection
- Lu Bing : Perception

# Timeline

\begin{figure}[htb]
\centering{\resizebox{1.02\textwidth}{!}{
  \begin{gantt}[xunitlength=0.9cm,drawledgerline=true]{11}{9}
    \begin{ganttitle}
    \titleelement{2016}{9}
    \end{ganttitle}
    \begin{ganttitle}
    \numtitle{4}{1}{12}{1}
    \end{ganttitle}
    \ganttbar{Discussion, Finalize Design}{0}{.5}
    \ganttbarcon{Purchasing \& Fabrication}{.5}{1}
    \ganttbarcon{Assembly and Mechatronics Tests}{1.5}{1.5}
    \ganttmilestone[color=cyan]{Robot Built!}{3}
    \ganttbar[color=cyan]{Developing Intelligence}{2.5}{2.5}
    \ganttbar{Localization and Navigation}{2.5}{2}
    \ganttbar{Vision, Object Detection}{3.5}{2}
    \ganttbar{Manipulation}{2.5}{3}
    \ganttmilestone{First Demo!}{6}
    \ganttcon{5}{6}{6}{10}
  \end{gantt}}
  }
\end{figure}

[\\]: <> (\ganttcon{4}{5}{4}{7})
[\\]: <> (\ganttbarcon{another consecutive task}{8}{.5})
