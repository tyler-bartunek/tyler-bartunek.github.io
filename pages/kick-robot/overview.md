---
layout: default
---
## What's a KICK Robot?
Formally, it's a novel open-source educational robotics platform under ongoing development by yours truly. I've been hosting my progress and the primary documentation on GitHub, though there's a little info here as well. 

Informally, it's the next step. 

The next step for:

1. People that have outgrown conventional robotics educational kits but aren't _quite_ ready for full-blown hardware design.
2. Tinkerers that want to rapidly and inexpensively prototype their mobile robot hardware.

Additionally, as an educational tool, you could say it's built for educators and researchers seeking to explore and explain controls and motion planning concepts on a budget.

KICK is an acronym, standing for **K**inematically **I**nterchangeable **C**ontrol **K**it.

### The Vision
Picture this: a 3D-printable kit that allows you to take a leftover shoebox, raspberry pi, and some other electronics, and get a mobile robot out of it.

With me so far? 

Did you picture your mobile robot as having wheels or legs? 

For the KICK robot I'm developing, you will be able to freely switch between the two (provided you have the right modules printed out) and change where they are attached to the box/robot body. You'll even be able to define your own means of locomotion and configurations for the modules you do have.

The KICK platform seeks to take things a step further than a lot of educational kits. A lot of existing kits have you build a pre-designed car or dog and your learning is almost entirely in the software domain.

The fun (and sometimes frustrating) thing about robots though, is that they don't exist entirely in the software domain. Aside from perhaps Lego kits or erector sets, there isn't as much exploration of the hardware side of things in a lot of kits out there. 

For instance, in a mecanum wheel-driven system, the layout and configuration of your wheels have a profound effect on the maneuvering capabilities of your robot. The same is actually very much true for 4-legged robots, though in that case you'll never see the layout that gives you better balance on uneven terrain in kits or commercial bots because it's said to be harder to manufacture.

A lot of control algorithms also assume a specific layout for your actuators. What if you break those assumptions? You can do that with the KICK Robot.

### More Info

<div style="display: flex; align-items: stretch; flex-wrap: wrap; gap: 16px;">

<!-- Project Status -->
{% include project-preview.html
    title="Project Status"
    description="Current status of development as of June ??, 2026"
    url="/pages/kick-robot/status.html"
%}

<!-- Architecture -->
{% include project-preview.html
    title="Architecture"
    image="/assets/img/kick-robot/ROS-graph.png"
    description="A high-level overview of what makes the KICK Robot tick, and instructions on how to build on the foundation I've laid."
    url="/pages/kick-robot/architecture.html"
%}

</div>