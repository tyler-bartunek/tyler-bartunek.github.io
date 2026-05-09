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

<!-- TODO: Create a diagram of the intended layout -->
<div style="text-align: center;">
<img src="{{ '/assets/img/kick-robot/ROS-graph.png' | relative_url}}" alt="ROS Graph" style="width: 100%;">
</div>

The KICK Robot platform in its basic form as seen above consists of at most four nodes. This is kept small to limit the number of transactions taking place across nodes using the ROS ecosystem, due to resource (RAM) constraints. 

1. Planner (swappable, future work): Generates movement commands, sends them to kickbrain over a command topic. 
2. kickbot: Central node, accepts input from battery_monitoring and the motion planner. Triggers a system halt and/or shutdown when power levels get too low, detects configurations based on module connections, and implements the control loop. 
3. bus\_hub: Polls each of the connection locations on the custom SPI Board, and manages transactions including error-checking via a checksum and a basic heartbeat message from the module (that the path and module ID are returned successfully on each transaction).
4. battery\_monitor: Monitors battery levels using an external 16-bit ADC and voltage divider circuit. 

#### Configurations
The software is written in a way to facilitate users writing their own custom kinematic configuration files for the kickbot node to use. Within the kickbrain package definition in the src folder (kickbrain/kickbrain), you'll find a configuration\_files folder. 

You write your custom kinematic configuration within this folder as a py file, and define it as a class that inherits from the Configuration base class. Each custom kinematic configuration needs to be defined as a class within their own .py file within the configuration\_files directory, and must contain the following methods with these signatures.

```
def fetch_commands(self, vel_cmd: Twist, feedback) -> list:
```

This method takes the center of mass velocity command from the motion planning node, which uses the built-in geometry\_msgs.Twist topic message type and any feedback to compute new actuator commands. 

``` 
def compute_received(self, device_data) -> Twist:
```
This method takes the data received from the bus\_hub node and computes the forward kinematics for your configuration to build feedback. 

Once you have your configuration kinematics defined, you go to the \_\_init\_\_.py file within the configuration\_files directory and add the frozenset of module ids that can be used to recognize your configuration. Note that it does use a frozenset, so if you need X number of modules for a successful deployment, be sure to add that check to your custom configuration's class definition.

__**Note that 0x00 is reserved as the "no connection" module ID, so your frozenset will need to include it if any connection points on the harness are disconnected**__

#### Modules
Similarly, the module code is written in a way to facilitate users writing their own custom module definitions. In fact, it's a conceptually identical process. 

The core code to deploy on the pico for each module is organized as follows:

1. modules
2. utils
3. main.cpp

You define your custom module by adding a header and cpp file within the modules subdirectory, and be sure to add the relevant files to the CMakeLists.txt file within that subdirectory. The custom module class that you define **must** inherit from the Module base class, and must include a run method override that defines your module's behavior in response to received data from the Pi. That run method **must** call `this -> transfer(data)`, where `data` is a short (uint16\_t) being sent back to the pi. 

Minimally viable example of a custom subclass header file:
```
#pragma once

#include "Module.h"

class MinimalExample : public Module {
    
    public:
        
        MinimalExample();

        void run() override;

        ~MinimalExample() = default;
};
```

If your module requires additional custom header files to function, these go under the utils subdirectory and you will in turn need to modify that CMakeLists.txt file.

For example, if you need to add something for the module to read an encoder that you've either written or cloned a library for named MyReallyCoolEncLib, you would modify the very first line of CMakeLists.txt file in utils to read:

```
add_library(utils STATIC SPITools.cpp MyReallyCoolEncLib.cpp)
```

assuming that your library has a cpp file defined for it.

Lastly, you modify line 18 of main.cpp to have the name of your new module type

```
#define MODULE_TYPE MinimalExample
```

**You must also define a custom module ID for your custom module instance, which you insert in your cpp file as you initialize the Module base class**

Currently used ID's within KICK framework:

| ID | Module Type |
|----|-------------|
|0x00 | Reserved, No Connection |
|0x01 | Echo test functionality |
|0x02 | Mecanum Wheel Version A |
|0x03 | Mecanum Wheel Version B |
|0x04 | Quadruped Leg Version A |
|0x05 | Quadruped Leg Version B |