---
title: Automatic Mapping
author: Saputra V.B.
date: Jun 30, 2016
---



[\\]: <> (date: Mar 17, 2016)


# Timeline

\begin{figure}[htb]
\centering{\resizebox{1.02\textwidth}{!}{
  \begin{gantt}[xunitlength=0.9cm,drawledgerline=true]{12}{6}
    \begin{ganttitle}
    \titleelement{2016}{6}
    \end{ganttitle}
    \begin{ganttitle}
    \numtitle{7}{1}{12}{1}
    \end{ganttitle}
    \ganttbar{Discussion, Finalize Design}{0}{.5}
    \ganttbarcon{Reimplementation Basic SLAM on New Robot}{.5}{1}
    \ganttbarcon{Testing with Navigation}{1.5}{1.5}
    \ganttmilestone[color=cyan]{Robot Base Built!}{1}
    \ganttbar[color=cyan]{Data Collection for Mapping}{1.5}{1.5}
    \ganttbar{Exploring and Implementation of Relocalization}{1.5}{2}
    \ganttbar{3D Mapping}{2.5}{2}
    \ganttbar{Dynamic Object Rejection}{1.5}{3}
    \ganttmilestone{First Demo!}{3}
    \ganttmilestone{Second Demo!}{5}
    \ganttcon{3}{6}{3}{10}
    \ganttcon{3}{10}{5}{11}
  \end{gantt}}
  }
\end{figure}

[\\]: <> (\ganttcon{4}{5}{4}{7})
[\\]: <> (\ganttbarcon{another consecutive task}{8}{.5})
