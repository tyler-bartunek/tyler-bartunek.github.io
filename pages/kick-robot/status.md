---
layout: default
title: Status Page
breadcrumb: 
  - title: Home
    url: /index.html
  - title: KICK Overview
    url: /pages/kick-robot/overview.html
---
## Project Status as of October 30, 2026

For the most up-to-date status and documentation for this project, refer to [the repository](https://www.github.com/tyler-bartunek/KICK-Robot/) and [the wiki](https://www.github.com/tyler-bartunek/KICK-Robot/wiki).

Milestone pages are under construction, and will gain more material with time. 

The current milestone focuses on on the software, namely getting the Desktop GUI for configuring robot and module-level settings as well as issuing velocity commands up and running. As of now, it finds the "robot" (raspberyy pi) and receives valid data from the ROS nodes.

Once that is done, the central electronics mount redesign will be wrapped up, printed off, and we can start looking at a whole-systems test. 

### Milestones

| Milestone # | Description | Status |
|-------------|-------------|--------|
| 0 | Actuator selection, characterization and filter design | Complete | 
| 1 | SPI hub board design and transaction integrity tests | Complete |
| 2 | ROS dev 1: Echo and basic motor control testing | Complete |
| 3 | GUI dev 1: Detecting devices and reading rosout | Complete |
| **4** | **GUI dev 2: Wireless motor control demo** | **Ongoing** |
| 5 | System test 1: Power distribution and monitoring | Future |
| 6 | System test 2: Manual mecanum teleoperation | Future |
| 7 | Hardware rev 2: Simplify assembly process and lower costs | Future |

As we get nearer to milestone 7's completion, more milestones will be planned out and added to the scope. The determination at that time will be whether to focus on fleshing out more perceptual capabilities and develop towards SLAM or to expand into 4-legged configurations. Present thought is to expand to 4-legged operation. 

#### Completed Milestones

[Milestone 0]({% link pages/kick-robot/milestones/milestone-0.md %}) <br>
[Milestone 1]({% link pages/kick-robot/milestones/milestone-1.md %}) <br>
[Milestone 2]({% link pages/kick-robot/milestones/milestone-2.md %}) <br>
[Milestone 3]({% link pages/kick-robot/milestones/milestone-3.md %})

#### Current Progress
[Milestone 4]({% link pages/kick-robot/milestones/milestone-4.md %})

#### Future Milestones
[Milestone 5]({% link pages/kick-robot/milestones/milestone-5.md %}) <br>
[Milestone 6]({% link pages/kick-robot/milestones/milestone-6.md %}) <br>
[Milestone 7]({% link pages/kick-robot/milestones/milestone-7.md %}) 

<br><br>
<a href="/pages/kick-robot/overview.html">Back to Overview</a>