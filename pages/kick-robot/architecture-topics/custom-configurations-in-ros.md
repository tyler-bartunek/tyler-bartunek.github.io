---
layout: default
---

[Back to Overview]({% link pages/kick-robot/overview.md %}) <br>
[Back to Architecture]({% link pages/kick-robot/architecture.md %}) <br>

## Writing Custom Configuration Files in ROS

To facilitate users writing their own custom kinematic configuration files for the kickbot node to use, the base KICK robot software for the Pi provides a base kick\_configs ROS package. Within this package is the Configuration base class that all configurations inherit from.

This makes things simpler from a standpoint of underlays and overlays, as is common in traditional ROS development. In order to add a configuration, it is recommended that you create an overlay that redefines the kick\_configs package to include your new configuration and also contains a copy of the kickbrain package. Future work will automate this for convenience. 

When writing a new configuration, the .py file contains a class definition that inherits from the Configuration base class and must contain corresponding overrides for the abstract methods.
```
class Configuration(ABC):

    def __init__(self, node, active_paths, device_ids):
    
        #Constructor code for the base class

    @abstractmethod
    def fetch_commands(self, vel_cmd: Twist, feedback) -> list:

        pass #Computes new actuator commands
        
    
    @abstractmethod
    def compute_received(self, device_data) -> Twist:

        pass #Computes the forward kinematics to close the control loop
``` 

Once you have your configuration kinematics defined, you go to the \_\_init\_\_.py file within the kick\_configs package and add the frozenset of module ids that can be used to recognize your configuration. Note that it does use a frozenset, so if you need X number of modules for a successful deployment, be sure to add that check to your custom configuration's class definition.

__**Note that 0x00 is reserved as the "no connection" module ID, so your frozenset will need to include it if any connection points on the harness are disconnected**__

<br>
[Back to Overview]({% link pages/kick-robot/overview.md %}) <br>
[Back to Architecture]({% link pages/kick-robot/architecture.md %})