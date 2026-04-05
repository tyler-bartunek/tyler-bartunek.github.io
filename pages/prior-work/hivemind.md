---
layout: default
---

## Haptic Interface for Drone Swarm Control

### Overview
In this class-based team project, I co-developed a tilt-based controller for quadcopter drones that provides haptic feedback to aid the user with obstacle avoidance. We evaluated how interpretable the provided cues were with a small pilot group of our classmates, and my partner built a ROS simulation where it was used to guide three crazyflie drones through an obstacle course.

### Background
When one thinks about quadcopter drones, they likely envision people using such devices for either recreational or creative purposes. However, they are also becoming increasingly popular for other activities including construction, regular maintenance/inspection, as well as search and rescue [1-3]. Regardless of use, obstacle avoidance is imperative for successful operation. Additionally, a consideration in applications with an operator in the loop is the usability of the interface where many operators can be confused with some options available [4-6]. Research has been done into tackling both problems, and related work has been cited at the bottom of this page. One finding in this research [4,5] was that when one uses hand-tilt based control devices and add haptic feedback, you achieve a highly intuitive interface with better outcomes for navigating confined spaces successfully. 

### The HIVE MIND: Proposed Prototype
The research into finding intuitive user interfaces as well as incorporating haptic feedback, at the time of this project, were limited to single-device systems. This project sought to extend this work into "drone swarms", or multi-drone systems. Another objective was to create a device that could simply be picked up, as opposed to the glove in prior work that has to be worn. 

Enter the HIVE MIND, or **H**andheld **I**nteractive **V**ibrotactil**e** **M**anipulandum for **I**nterfacing with **N**umerous **D**rones, pictured below.

<div style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_front.png' | relative_url }}" alt="HIVEMIND" style="width: 50%;"/>
</div>

This prototype device used a BNO055 IMU for detecting tilt commands and the knob on the side for controlling swarm density, or how close the drones would fly next to each other. It would control a lead drone, and all other drones in the swarm behaved as follower devices. Whenever a collision event was detected as likely, the 6 vibrotactile motors along the front edge of the device or the provided band that would fit over the back of the user's hand corresponding with the direction of collision would vibrate according to this strategy.

<div style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_directional_cues.png' | relative_url }}" alt="directional cues" style="width: 75%;">
</div>

### Evaluation
This prototype was initially evaluated in terms of whether or not its vibrotactile feedback could be parsed by the user. A double-blind study was designed where each user would receive a cue using the device and they would have to select on a screen which of the squares they believed corresponded with the provided cue. The squares did not have the labels provided in this image, those labels are provided for your convenience and map onto abbreviations for either close or far. For example, 'FLF' would be 'Front Left Far'. 

<div sytle="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_evaluation_key.png' | relative_url }}" alt="user options" style="width: 75%;">
</div>

Accuracy scores were compiled for each user, and it was determined that users could generally determine overall directions of feedback, but proximity was a little more confusing. Even then, there were still notable moments of confusion with the cues corresponding to directly lateral collisions. 

<div style="text-align: center">
<img src="{{ 'assets/img/hive_mind/hive_mind_confusion.png' | relative_url }}" alt="confusion" style="width:100%;">
</div>

We also received some subjective feedback about the dimensions of the device, namely that it was a little on the large side since the frontal cues worked best if your fingers were directly over the motors. Overall, it was conclude that the design needs to be iterated upon. 

The other core functionality of the device was if the tilt commands and knob were intuitive. For this, my project partner build a ROS2 simulation (Foxy Fitzroy) using Webots to simulate 3 crazyflie drones.  

<div style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_evaluation_ros.png' | relative_url }}" alt="ros sim" style="width: 75%;"/>
</div>

This test was more warmly received, with users describing it as fun though challenging. Especially launch since the controller immediately started doing its job, leading to a lot of crashes during takeoff. 

### Future Work
Based on feedback, future directions for this project would center upon better mechanically separating the motors from each other, as the vibrations carrying through the 3D printed (PLA) body led to confusion. A just noticeable difference study would also help in ensuring that the vibration algorithm would produce more distinguishable cues. Lastly, dimensions (notably the width and height) would be reduced. 

One possible design under consideration would place motors onto thimbles connected by retractable reels connected to the main body of the controller. Other possible designs would involve some amount of relaxing the 'device you can pick up' constraint and/or deploying pseudohaptics in VR to help.

### Related Work/Citations
1. D. Kim and P. Y. Oh, “Aerial manipulation using a human-embodied
drone interface,” in _2022 IEEE International Conference on Advanced
Robotics and Its Social Impacts (ARSO)_, pp. 1–7, 2022.
2. J. Cacace, A. Finzi, V. Lippiello, M. Furci, N. Mimmo, and L. Marconi,
“A control architecture for multiple drones operated via multimodal interaction
in search & rescue mission,” _2016 IEEE International Symposium
on Safety, Security, and Rescue Robotics (SSRR)_, pp. 233–239, 2016.
3. A. Ollero, M. Tognon, A. Suarez, D. Lee, and A. Franchi, “Past, present,
and future of aerial robotic manipulators,” _IEEE Transactions on Robotics_,
vol. 38, no. 1, pp. 626–645, 2022.
4. M. Macchini, T. Havy, A. Weber, F. Schiano, and D. Floreano, “Handworn
haptic interface for drone teleoperation,” in _2020 IEEE International
Conference on Robotics and Automation (ICRA)_, pp. 10212–10218, 2020.
5. M. Macchini, J. Frogg, F. Schiano, and D. Floreano, “Does spontaneous
motion lead to intuitive body-machine interfaces? a fitness study of
different body segments for wearable telerobotics,” in _2022 31st IEEE
International Conference on Robot and Human Interactive Communication
(RO-MAN)_, pp. 115–121, 2022.
6. E. Tsykunov, R. Agishev, R. Ibrahimov, L. Labazanova, A. Tleugazy, and
D. Tsetserukou, “Swarmtouch: Guiding a swarm of micro-quadrotors with
impedance control using a wearable tactile interface,” _IEEE Transactions
on Haptics_, vol. 12, no. 3, pp. 363–374, 2019.

**Pending: work by supervising professor presented in 2026 World Haptics**