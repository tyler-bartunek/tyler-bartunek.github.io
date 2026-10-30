---
layout: default
title: Milestone 2
breadcrumb:
  - title: Home
    url: /index.html
  - title: KICK Overview
    url: /pages/kick-robot/overview.html
  - title: Status
    url: /pages/kick-robot/status.html
---

## Milestone 2: ROS Framework

### What this has entailed
1. ROS nodes for transmitting and receiving valid commands and feedback runs without errors. 
2. Module code written in C++ using the Pico SDK, correctly handshakes with the Pi and status indicator changes from "disconnected" to "all clear" sequence. 
3. Additional ROS nodes for battery monitoring and a full systems check have been written.
4. Pico integration with the DRV8871 motor drivers and encoder reading functionality, test case for ROS runs without major errors.
5. Velocity jacobian math has been worked out, partial implementation built within configuration class definition.

**Detailed write-up in progress, stay tuned!**

### Room for improvement (future milestones)
1. Need the Pico to recognize when it has lost the Pi. 