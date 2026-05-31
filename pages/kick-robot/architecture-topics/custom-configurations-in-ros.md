---
layout: default
---
## Writing Custom Configuration Files in ROS

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