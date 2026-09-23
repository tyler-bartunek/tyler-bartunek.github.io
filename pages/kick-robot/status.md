---
layout: default
---
## Project Status as of September 23, 2026

For the most up-to-date status and documentation for this project, refer to [the repository](https://www.github.com/tyler-bartunek/KICK-Robot/) and [the wiki](https://www.github.com/tyler-bartunek/KICK-Robot/wiki).

Current focus is on the [Software](#software), namely getting the Desktop GUI for configuring robot and module-level settings as well as issuing velocity commands up and running. As of now, it finds the "robot" (raspberyy pi) and receives valid data from the ROS nodes.

Once that is done, the central electronics mount design will be wrapped up, printed off, and we can start looking at a whole-systems test. 

### Hardware

#### Complete
1. Motors + Wheel combos characterized, physical parameters calculated, low-pass filter tuned for velocity feedback.
2. Prototype SPI distribution board finished basic echo transaction testing, found transactions at up to 6 MHz clock speeds are feasible.
3. Initial rev of hardware mounts (rails and wheel module motor mounts) printed and assembled on box.
4. Mounts for basic power circuitry designed; fuses, fuse holders, and battery connectors have been acquired.

#### Ongoing
Redesign of central electronics mount for raspberry pi and SPI board. This will naturally lead to an updated render of the completed assembly.

#### Future
1. Tweaking of mounting clip and plate dimensions for better assembly experience.
2. Wheel module assembly and testing. 
3. Leg module development.

### Software

#### Complete
1. ROS nodes for transmitting and receiving valid commands and feedback runs without errors. 
2. Module code written in C++ using the Pico SDK, correctly handshakes with the Pi and status indicator changes from "disconnected" to "all clear" sequence. 
3. Additional ROS nodes for battery monitoring and a full systems check have been written.
4. Pico integration with the DRV8871 motor drivers and encoder reading functionality, test case for ROS runs without major errors.
5. Desktop GUI discovers the "kickbot" on the Wi-Fi network (mDNS zero configuration service discovery), connects, and receives data from the robot (rosbridge). 


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