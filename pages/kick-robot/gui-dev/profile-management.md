---
layout: default
---

<a href="/pages/kick-robot/overview.html">Back to Overview</a> <br>
<a href="/pages/kick-robot/gui-dev/desktop-gui.html">Back to GUI development home</a>

## Robot Profile Management

All robots are managed through a combination of three tools that work in harmony with each other: 

    1. RobotProfileManager: Manages RobotProfile data class instances for each bot.
    2. SessionManager: Manages the interaction each bot has with the control algorithm of choice (in progress).
    3. AvailabilityMonitor: Pings each bot to check on their connection status via socket. 

That third tool largely does nothing during regular robot operation, and will not be a focus of this writeup. 

## RobotProfile
The profile management system within the GUI is mostly in charge of handling the RobotProfile data class. This data class simply tracks the robot's:

    1. Hostname
    2. Port
    3. IP address
    4. Focus status
    5. Workspace (currently optional)
    6. Bridge availability (works with availability monitoring), and
    7. Connected device locations

Most of these just cover basic logistics for forming a connection, and are set up to be saved in json format at a later point for users to load in. While that functionality has not been fully fleshed out yet, that is a forward-looking goal to allow users to have some degree of persistence from one power cycle of the bot to the next. Future work may allow for saving additional settings, but this is what is being saved for now.

The focus status and bridge availability have additional functional purpose. The goal for the GUI is to support multiple connected devices, but the nature of the interface presupposes that you are only actually changing settings for one device at any given moment. This is what the focus status flag is intended to track.

Bridge availability works in tandem with the AvailabilityMonitor for that robot to keep track of connection status and shut down connections within the GUI if we lose the device. Basically a safety feature more than anything else. 

### Rosbridge Attribute Control
The manager class for these profiles stores each profile object in a list, and also maintains a dictionary containing the ROS_StreamWorker objects responsible for maintaining connections with the robot at the corresponding hostname. 

In addition to simply having the dictionary attribute tracking which stream workers go with which robot, it also has methods for fetching the worker as well as changing the device focus flag.

Instead of terminating the rosbridge and logging connection when the device focus shifts, it maintains the connection until the GUI is closed. Future work may involve an option to sever the connection entirely, but that is out-of-scope for now until basic planning/multi-device functionality is demonstrated.

## Control Sessions
Keeping in mind that the system maintains connections to each robot even when it isn't the focused device, the session manager keeps track of the control session for each bot. Each session simply keeps track of each robot's rosbridge and the associated planner currently in charge of controlling the bot. 

For now, the only planner being implemented is manual keypad control, with progress still ongoing towards having the signals wired appropriately. Upon that succeeding, attention will shift to more automated control algorithms. This future work will likely turn toward OMPL for some existing implementations to build upon. 

All control algorithms at present are going to be velocity-based, because that is how the kickbrain is presently wired. Future work may explore other possibilities, but velocity control makes sense to me for a mobile robot navigating based on keypad commands. 