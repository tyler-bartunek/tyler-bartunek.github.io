---
layout: default
---
## What's a KICK Robot?
In short, it's a novel open-source platform under ongoing development by yours truly. I've been hosting my progress and the primary documentation on GitHub, though there's a little info here as well. 

KICK is an acronym, standing for **K**inematically **I**nterchangeable **C**ontrol **K**it.

What does that mean?

Picture this: a 3D-printable kit that allows you to take a leftover shoebox, raspberry pi, and some other electronics, and get a mobile robot out of it.

With me so far? 

Did you picture your mobile robot as having wheels or legs? 

For the KICK robot I'm developing, you will be able to freely switch between the two (provided you have the right modules printed out) and change where they are attached to the box/robot body. You'll even be able to define your own means of locomotion and configurations for the modules you do have.

One might ask "aren't there a lot of kits that have this same general goal?", and that is a fair criticism. However, the KICK platform seeks to take things a step further. A lot of existing kits have you build a pre-designed car or dog and your learning is almost entirely in the software domain.

The fun (and sometimes frustrating) thing about robots though, is that they don't exist entirely in the software domain. Aside from perhaps Lego kits or erector sets, there isn't as much exploration of the hardware side of things. 

For instance, in a mecanum wheel-driven system, the layout and configuration of your wheels have a profound effect on the maneuvering capabilities of your robot. The same is actually very much true for 4-legged robots, though in that case you'll never see the layout that gives you better balance on uneven terrain in kits or commercial bots because it's harder to manufacture.

A lot of control algorithms also assume a specific layout for your actuators. What if you break those assumptions? You can do that with the KICK Robot.

## Project Status as of May 9, 2026

For the most up-to-date status and documentation for this project, refer to [the repository](https://www.github.com/tyler-bartunek/KICK-Robot/) and [the wiki](https://www.github.com/tyler-bartunek/KICK-Robot/wiki).

### Hardware

#### Complete
1. Motors + Wheel combos characterized, physical parameters calculated, low-pass filter tuned for velocity feedback.
2. Prototype SPI distribution board finished basic echo transaction testing, found transactions at up to 6 MHz clock speeds are feasible.
3. Initial rev of hardware mounts (rails and wheel module motor mounts) printed and assembled on box.

#### Ongoing
Redesign of central electronics mount for raspberry pi, SPI board, batteries, and power circuitry. This will naturally lead to an updated render of the completed assembly.

#### Future
1. Tweaking of mounting clip and plate dimensions for better assembly experience.
2. Wheel module assembly and testing. 

### Software

#### Complete
1. ROS nodes for transmitting and receiving valid commands and feedback runs without errors. 
2. Module code written in C++ using the Pico SDK, correctly handshakes with the Pi and status indicator changes from "disconnected" to "all clear" sequence. 
3. Additional ROS nodes for battery monitoring and a full systems check have been written.

#### Ongoing
1. Pico integration with the DRV8871 motor drivers and encoder reading functionality.
2. Recognition on the module side for when the host has been lost.

#### Future
1. Battery monitoring testing
2. Desktop GUI for configuring more fine-tuned robot settings, such as specific module connection locations and rail separation distance. 
3. Full implementation and testing of two layout configurations for mecanum wheels. 