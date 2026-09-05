---
layout: default
---
## What's a KICK Robot?
KICK is an acronym, standing for **K**inematically **I**nterchangeable **C**ontrol **K**it.

Formally, it's a novel open-source educational robotics platform under ongoing development by yours truly. I've been hosting my progress and the primary documentation on [GitHub](https://www.github.com/tyler-bartunek/KICK-Robot/), though there's a little info here as well. 

Informally, it's the next step for:

1. People that have outgrown conventional robotics educational kits but aren't _quite_ ready for full-blown hardware design.
2. Tinkerers that want to rapidly and inexpensively prototype their mobile robot hardware.

Additionally, as an educational tool, you could say it's built for educators and researchers seeking to explore and explain controls and motion planning concepts on a budget.

It's also a play on words, since "kicks" are another word for shoes, and the robot is made out of a shoebox.

### The Vision
Picture this: a 3D-printable kit that allows you to take a leftover shoebox, raspberry pi, as well as some other electronics, and get a mobile robot out of it.

With me so far? 

Did you picture your mobile robot as having wheels or legs? 

For the KICK robot I'm developing, you will be able to freely switch between the two (provided you have the right modules printed out) and change where they are attached to the box/robot body. You'll even be able to define new configurations for your existing modules or come up with new locomotion modules altogether.

The KICK platform seeks to take things a step further than a lot of educational kits. A lot of existing kits choose to either go in-depth in hardware **or** software, but not both. This kit seeks to target both, so you gain a complete and intuitive sense for the levers you can pull as a roboticist to change system behavior.

For instance, in a mecanum wheel-driven system, the layout and configuration of your wheels have a profound effect on the maneuvering capabilities of your robot. The same is actually very much true for 4-legged robots, though in that case you'll never see the layout that gives you better balance on uneven terrain in kits or commercial bots because it's said to be harder to manufacture.

A lot of control algorithms also assume a specific layout for your actuators. What if you break those assumptions? You can do that with the KICK Robot.

### More Info

<div style="display: flex; align-items: stretch; flex-wrap: wrap; gap: 16px;">

<!-- Project Status -->
{% include project-preview.html
    title="Project Status"
    image="/assets/img/Updated_KICK_logo.png"
    description="Current status of development as of September 4, 2026"
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
<!-- {% include project-preview.html
    title="Desktop Application Notes"
    description="Development notes for the user interface being developed for controlling robot settings."
    url="/pages/kick-robot/gui-dev/desktop-gui.html"
%} -->

</div>