---
layout: default
---
## Project Status as of September 4, 2026

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
4. Pico integration with the DRV8871 motor drivers and encoder reading functionality, test case for ROS runs without major errors.
5. Desktop GUI connects with Raspberry Pi ROS2 code via mDNS discovery and communicates via rosbridge.


#### Ongoing
1. Recognition on the module side for when the host has been lost.
2. Desktop GUI
   - Sending commands to the robot
   - Changing robot, sensor, and module-level settings


#### Future
1. Battery monitoring testing
2. Full implementation and testing of two layout configurations for mecanum wheels. 

<br><br>
<a href="/pages/kick-robot/overview.html">Back to Overview</a>