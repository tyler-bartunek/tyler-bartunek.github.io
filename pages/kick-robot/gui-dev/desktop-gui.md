---
layout: default
---

<a href="/pages/kick-robot/overview.html">Back to Overview</a> <br>

## Desktop GUI

I've been developing an application for configuring and altering settings for the KICK robot using PyQt6. As of [now]({% link pages/kick-robot/status.md %}), this application looks like:

<!-- Insert screen capture of the GUI -->
<div style="text-align: center;">
<img src="{{ '/assets/img/kick-robot/KICK-GUI-screen.png' | relative_url}}" alt="compressive redesign" style="width: 100%;">
</div>

### Current Work

As of the last update, wiring up the backend of the application is well underway.

#### Currently Functional

1. Logging <br>
    a. Subscribed to rosout topic and streaming log messages to the user. <br>
    b. Also provides GUI-side status updates.
2. Status cards <br>
    a. Battery: Appropriately displays hard-coded test value and percentage. <br>
    b. Loop: Provides an estimate of loop frequency in Hz based on bot-state subscription message rate. <br>
    c. Cmd_vel active: Reports that the GUI has publishing capability to the robot
3. Robot selection dropdown and connection status indicator <br>
    a. Connection button toggles correctly between 'Connect'/'Disconnect' states (can't attempt connection before device is ready). <br>
    b. 'Disconnect' disconnects status card signals and changes connection status. <br>
4. Toggling between central canvases (Hardware Configuration, Sensor Settings, SLAM placeholder) 
5. Sensor names added to active list, settings persist between dialog box opening/closing <br>
    a. This includes functionality related to pulling XML-defined sensor parameters into that settings dialog box. <br>
6. Manual Control
   - D-pad updates velocity commands appropriately.
7. Checking for exit confirmation before closing.


#### Current Focus

1. Manual control
   - Connecting Keyboard
   - Initial PID on Pi-side for hot motor test

<!-- #### Currently Suspect/Buggy

Bold denotes primary focus

1. **Control: Keyboard functionality currently unresponsive.**
2. Connected Modules Status Card: Logging tells us there should be erroneously detected modules, but device count doesn't update. This could go either way, the lower update rate of bot-state relative to bus-state could be smoothing out false positives. -->

#### Upcoming

1. Menubar across top of screen: provide redundant means to set the robot
2. Telemetry testing
3. Finishing touches/changes to the Rail Canvas to improve the user experience
4. Module placement
5. Parameter pushing: Some parameters defined on Pi side, need to write access on GUI side.    
6. Perception node implementations on Pi side, as well as launching from GUI side.

### Topics

<!-- ROS Bridge -->
<!-- {% include project-preview.html
    title="Rosbridge Robot Connection"
    description="Provides details on how the GUI communicates with the bot via rosbridge"
    url="/pages/kick-robot/gui-dev/rosbridge.html"
%} -->

<!-- Profile Management -->
{% include project-preview.html
    title="Plans for fleet management in the GUI"
    description="Gives an overview of current work building the GUI in a way that facilitates multi-robot operation."
    url="/pages/kick-robot/gui-dev/rosbridge.html"
%}

**More Coming Soon!**