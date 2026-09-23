---
layout: default
---
## Overview
&bull; [What's a KICK Robot?](#whats-a-kick-robot)  
&bull; [The Vision](#the-vision)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [What it Does](#what-it-does)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Why it Matters](#why-it-matters)  
&bull; [More Info](#more-info)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Topics](#topics)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Project Status](#topics)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Architecture](#topics)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Desktop Application Notes](#topics)  
&nbsp;&nbsp;&nbsp;&nbsp;&bull; [Git Links](#git-links)

### What's a KICK Robot?
KICK is an acronym, standing for **K**inematically **I**nterchangeable **C**ontrol **K**it. The name is a play on words, since "kicks" are another word for shoes, and the robot is (optionally) made out of a shoebox.

Formally, it's a novel open-source educational robotics platform under ongoing development by yours truly. It is my most ambitious project to-date, involving full-stack (hardware + software) development and has led to learning new skills like the basics of PCB design, ROS2, and basic desktop application development in PyQt. See [The Vision](#the-vision) for more details, and [Git Links](#git-links) for repository links.

Informally, it's the next step for:

1. People that have outgrown conventional robotics educational kits but aren't _quite_ ready for full-blown hardware design.
2. Tinkerers that want to rapidly and inexpensively prototype their mobile robot hardware.

Additionally, as an educational tool, you could say it's built for educators and researchers seeking to explain or explore controls and motion planning concepts on a budget.

### The Vision
<strong>TL;DR: A lot of educational kits choose to explore either hardware or software flexibility, but not both together. The KICK platform aims to do exactly this, and with a user-friendly interface and a low cost (current prototype is under $300). By its nature, it is an evergreen project. </strong><br>

#### What it does
The KICK platform seeks to take things a step further than a lot of educational kits. A lot of existing kits choose to either go in-depth in hardware _**or**_ software, but not both. This kit seeks to target both, so you gain a complete and intuitive sense for the levers you can pull as a roboticist to change system behavior.

Picture this: a 3D-printable kit that allows you to take a leftover shoebox, raspberry pi, as well as some other electronics, and get a mobile robot out of it.

With me so far? 

Did you picture your mobile robot as having wheels or legs? 

<!--TODO: Add CAD render of robot -->

For the KICK robot I'm developing, you will be able to freely switch between the two (provided you have the right modules printed out) and change where they are attached to the box/robot body. You'll even be able to define new configurations for your existing modules or come up with new locomotion modules altogether. Additionally, you can also tweak the control algorithm, the motion planner, and kinematic parameters from a graphical user interface on your desktop. 

<!-- TODO: Add wheels module render as an example -->

The flexible nature of this project makes it hard to pick a hard cutoff for when I'll be "done" working on it. Since there will always be new locomotion modules to design and algorithms to implement, as well as ways to improve existing designs, I view this project as evergreen. Meaning it doesn't have a real end date, I'm more aiming for specific milestones than a tidy conclusion.

#### Why it matters
The layout, configuration, and dimensions of your wheels/legs have a profound effect on the maneuvering capabilities of your robot. KICK allows you to explore your design space with actual hardware.

A lot of control algorithms also assume a specific layout for your actuators. What if you break those assumptions? 

You can do that with the KICK Robot and its associated interface.

What's more important, you can do both in a way that circumvents the sim-to-real gap without breaking the bank. 

## More Info

### Topics
<div style="display: flex; align-items: stretch; flex-wrap: wrap; gap: 16px;">

<!-- Project Status -->
{% include project-preview.html
    title="Project Status"
    image="/assets/img/Updated_KICK_logo.png"
    description="Current status of development as of September 16, 2026"
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