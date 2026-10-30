---
layout: default
title: Project Home
breadcrumb:
  - title: Home
    url: /index.html
---
## Overview
&bull; [What's a KICK Robot?](#whats-a-kick-robot)  
&bull; [The Vision](#the-vision)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [What it does](#what-it-does)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Who it's for](#who-its-for)  
&bull; [More Info](#more-info)   
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Project Status](#topics)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Architecture](#topics)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Desktop Application Notes](#topics)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Git Links](#git-links)

<!-- - [What's a KICK Robot](#whats-a-kick-robot)
- [The Vision](#the-vision)
  - [What it does](#what-it-does)
  - [Who it's for](#who-its-for)
- [More Info](#more-info)
- [Topics](#topics)
  - [Project Status](#topics)
  - [Architecture](#topics)
  - [Desktop Application Notes](#topics)
  - [Git Links](#links) -->

### What's a KICK Robot?
KICK is an acronym, standing for **K**inematically **I**nterchangeable **C**ontrol **K**it. The name is a play on words, since "kicks" are another word for shoes, and the robot is (optionally) made out of a shoebox.

Formally, it's a novel open-source educational robotics platform under ongoing development by yours truly. It is my most ambitious project to-date, involving full-stack (hardware + software) development and has led to learning new skills like the basics of PCB design, ROS2, and basic desktop application development in PyQt. See [The Vision](#the-vision) for more details, and [Git Links](#git-links) for repository links.

### The Vision
<strong>TL;DR: Changing hardware layout or mode of locomotion often involves a complete rebuild of the whole project, but it doesn't have to be that way. The KICK platform aims to offer a "sandbox" that adapts to your hardware as it comes online, and with a user-friendly interface and a low cost (current prototype is under $300). Lots of room for ongoing development beyond the minimally viable prototype. </strong><br>

<!-- Insert video of demo -->

#### What it does
The beautiful thing about robotics is the intersection and interconnection of hardware and software. 

It's also one of the biggest pain points in prototyping. 

Specifically in one direction, the hardware to software consideration. Every hardware change (wheel spacing and arrangement, legs vs wheels, etc.) needs to come with a corresponding software change if you want the same behavior. 

The KICK platform seeks to address this issue, and do so inexpensively. 

It aims to do so through a three-pronged approach:
1. 3D-printable and modular hardware: A cardboard box-mountable rail system allows one to "freely" change actuator type and spacing along the bottom of the bot. 
2. A software framework implemented in both C++ and ROS that simplifies actuator module development.
3. A desktop application to make changing robot and module settings, as well as tweaking the control algorithm, simpler for those that don't want to SSH into the bot every time. This desktop application will also host the motion planner to reduce computational load on the bot, allowing a cheaper single board computer to be used as the brain.

Those last two are where the bulk of the ongoing work resides. For a more detailed view of the overall project status, check [the status page](#topics).

<!--TODO: Add CAD render of robot -->

The flexible nature of this project makes it so there will always be new locomotion modules to design and algorithms to implement. This means that instead of a fixed "end goal", development is segmented into milestones. The minimally viable prototype under development is the manual teleoperation mecanum wheel setup, which itself will support both "x" and "o" configurations of the wheels out of the box. 

#### Who it's for: 
KICK is for anyone that wants to make on-the-fly adjustments to their mobile robots without breaking the bank. The long-term goal is for the KICK system to be buildable with common hobby equipment (3D printer, soldering iron, off-the-shelf electronics).

## More Info

<div style="display: flex; align-items: stretch; flex-wrap: wrap; gap: 16px;">

<!-- Project Status -->
{% include project-preview.html
    title="Project Status"
    image="/assets/img/Updated_KICK_logo.png"
    description="Current status of development as of October 30, 2026"
    url="/pages/kick-robot/status.html"
%}

<!-- Architecture -->
{% include project-preview.html
    title="Architecture"
    image="/assets/img/kick-robot/ROS-graph.png"
    description="A high-level overview of what makes the KICK Robot tick, and instructions on how to build on the foundation I've laid."
    url="/pages/kick-robot/architecture.html"
%}

<!-- Desktop Application -->
{% include project-preview.html
    title="Desktop Application Notes"
    image="/assets/img/kick-robot/KICK-GUI-screen.png"
    description="Development notes for the user interface being developed for controlling robot settings."
    url="/pages/kick-robot/gui-dev/desktop-gui.html"
%}

</div><br>

### Git Links 

<div style="text-align: center">
<a href= "https://www.github.com/tyler-bartunek/KICK-Robot/"
   style="display: inline-block; background-color: #1e6bb8; color: #fff; padding: 10px 20px; text-decoration: none; margin: 5px">
  Main GitHub Repository
</a> 
<a href= "https://www.github.com/tyler-bartunek/KICK-Robot/wiki"
   style="display: inline-block; background-color: #1e6bb8; color: #fff; padding: 10px 20px; text-decoration: none; margin: 5px">
  Git Wiki
</a>
<a href= "https://www.github.com/tyler-bartunek/KICK_Pi/"
   style="display: inline-block; background-color: #1e6bb8; color: #fff; padding: 10px 20px; text-decoration: none; margin: 5px">
  Repository for the Pi stack
</a>
</div><br>