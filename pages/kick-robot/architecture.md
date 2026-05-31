---
layout: default
---

## Architecture

The KICK Robot system spans both hardware and software, and this page attempts to describe both architectures.

### Hardware
There are two pieces of hardware that serve as the heart and soul of the ShoeBot framework:
1. The SPI distribution board
2. The rail system

**More details coming soon, will be available on the [wiki](https://www.github.com/tyler-bartunek/KICK-Robot/wiki) first**

### Software
The core software of the ShoeBot (the stuff that will live on the raspberry pi) was developed using ROS, or robot operating system. At a future date, I might write a knowledge base article on more of the details of ROS for the uninitiated, but for now I will direct you to the [Open Robotics Documentation](https://docs.ros.org/en/jazzy/Concepts/Basic.html) if you want to learn more about it.

On the other side of the equation, you have the individual modules, which are being developed for the RPi Pico 2040 using the Pico's SDK. 

#### ROS Code
At a basic level, we have a set of points in a network that are connected by lines of communication. In ROS nomenclature, we have nodes connected via topics and a service. The basic network is shown below. 

<div style="text-align: center;">
<img src="{{ '/assets/img/kick-robot/ROS-graph.png' | relative_url}}" alt="ROS Graph" style="width: 100%;">
</div>

The KICK Robot platform in its basic form as seen above consists of at most four nodes. This is kept small to limit the number of transactions taking place across nodes using the ROS ecosystem, due to resource (RAM) constraints. 

1. Planner (swappable, future work): Generates movement commands, sends them to kickbrain over a command topic. 
2. kickbot: Central node, accepts input from battery_monitoring and the motion planner. Triggers a system halt and/or shutdown when power levels get too low, detects configurations based on module connections, and implements the control loop. 
3. bus\_hub: Polls each of the connection locations on the custom SPI Board, and manages transactions including error-checking via a checksum and a basic heartbeat message from the module (that the path and module ID are returned successfully on each transaction).
4. battery\_monitor: Monitors battery levels using an external 16-bit ADC and voltage divider circuit. 

#### Modules
The core code to deploy on the pico for each module is organized as follows:

1. modules
2. utils
3. main.cpp

Within main.cpp, the MODULE_TYPE is specified using the `#define` macro, and the relevant header file is where the module ID is set for use by the ROS code to identify the module.

Currently used ID's within KICK framework:

| ID | Module Type |
|----|-------------|
|0x00 | Reserved, No Connection |
|0x01 | Echo test functionality |
|0x02 | Mecanum Wheel Version A |
|0x03 | Mecanum Wheel Version B |
|0x04 | Quadruped Leg Version A |
|0x05 | Quadruped Leg Version B |

In the case of the Mecanum Wheel, if you need to change the code from Version A (Left) to Version B (Right), you need to go into the modules directory, find the "Wheels.cpp" file, and modify which one is defined by the `#define` macro. 

### More Info

These articles handle these topics in greater depth, as does the [wiki](https://www.github.com/tyler-bartunek/KICK-Robot/wiki).

<div style="display: flex; align-items: stretch; flex-wrap: wrap; gap: 16px;">

<!-- Custom Configurations in ROS -->
{% include project-preview.html
    title="Writing Custom Configurations"
    url="/pages/kick-robot/architecture-topics/custom-configurations-in-ros.html"
%}

<!-- Custom Module Definitions -->
{% include project-preview.html
    title="Writing Custom Module Definitions in the Pico SDK"
    url="/pages/kick-robot/architecture-topics/custom-modules-pico.html"
%}

<!-- Transmission -->
{% include project-preview.html
    title="Transmission To/From Modules"
    url="/pages/kick-robot/architecture-topics/transmission.html"
%}

</div>

[Back to Overview]({% link pages/kick-robot/overview.md %})