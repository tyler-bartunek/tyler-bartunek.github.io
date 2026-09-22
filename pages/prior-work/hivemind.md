---
layout: default
---

## Haptic Interface for Drone Swarm Control

<figure style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_evaluation_ros.png' | relative_url }}" alt="visual abstract" style="width: 75%;">
<figcaption style="font-size: 0.85em; color: #666;">Using the interface to control a simulated drone swarm, highlighted with red circles.</figcaption>
</figure>

<strong>Outcomes: </strong> 
- Submitted project report and earned an A.
- Demonstration was deemed "compelling" and shown to a collaborator, which may have informed elements of related work presented at the 2026 Haptics Symposium. <br>

<strong>Status: </strong> 
- Project ended in 2023. 
- Prototype left with H-CHAR lab
- Simulation and data analysis code repositories provided as part of project deliverable (the report). <br>

<strong>Skills: </strong> SolidWorks, Rapid Prototyping, C++, Mechatronics, Experimental Design, Haptics 


### Overview
In this class-based team project, I co-developed a tilt-based controller for quadcopter drones that provides haptic feedback to aid the user with obstacle avoidance. We evaluated how interpretable the provided cues were with a small pilot test with our classmates, and my partner built a ROS simulation where the device was used to guide three crazyflie drones through an obstacle course.

### Background
When one thinks about quadcopter drones, they likely envision people using such devices for either recreational or creative purposes such as videography. However, they are also becoming increasingly popular for other activities including construction, regular maintenance/inspection, as well as search and rescue [1-3]. Regardless of use, obstacle avoidance remains imperative for successful operation. Additionally, a consideration in applications with an operator in the loop is the usability of the interface, with many systems having operators report confusion during use [4-6]. Research has been conducted on obstacle avoidance and interface usability, and selected work has been cited at the bottom of this page. One finding in this research [4,5] was that when one combines interfaces that command the drones based on tilting the hand with haptic feedback, you achieve a highly intuitive interface with better outcomes for navigating confined spaces successfully. 

### The HIVE MIND: Proposed Prototype
At the time of this project, work with tilt-based systems providing haptic feedback was limited to single-drone systems. This project sought to extend this work into "drone swarms", or multi-drone systems. Another objective was to create a device that could simply be picked up, as opposed to glove-based systems that must be worn. This was seen as an improvement in convenience for the user. 

Enter the HIVE MIND, or **H**andheld **I**nteractive **V**ibrotactil**e** **M**anipulandum for **I**nterfacing with **N**umerous **D**rones, pictured below. Yes, the name was my idea.

<div style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_front.png' | relative_url }}" alt="HIVEMIND" style="width: 50%;"/>
</div>

This prototype device used a BNO055 IMU for detecting tilt commands and the knob on the side for controlling swarm density, or how close the drones would fly next to each other. It would control a lead drone, and all other drones in the swarm behaved as follower devices. Whenever a collision event was detected as likely, the 6 vibrotactile motors along the front edge of the device and/or the band that fit over the back of the user's hand would vibrate in a pattern consistent with the direction and immediacy of collision, with directional cues shown graphically below.

<div style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_directional_cues.png' | relative_url }}" alt="directional cues" style="width: 100%;">
</div>

### Evaluation
This prototype was initially evaluated in terms of how interpretable the vibrotactile feedback was for users. A double-blind study was designed where each user would receive a cue using the device and they would have to select on a screen which of the squares they believed corresponded with the provided cue. In this image, the green square represented the location of the drone and white squares were eligible options. The labels were not visible on their screen, but correspond to a later graphic and map onto abbreviations for either close or far. For example, 'FLF' would be 'Front Left Far'. 

<div style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_evaluation_key.png' | relative_url }}" alt="user options" style="width: 65%;">
</div>

Accuracy scores were compiled for all users, as well as confusion matrices. Now, among the 5 users that got to test the device, two of them were myself and my project partner. For purposes of integrity, and also because of the interesting story told by these figures, results between us and "novice" users are shown both separately and together. The confusion matrix provided shows the aggregate. Putting these results in context, random guessing would score an accuracy of 6.25%. N is the number of users, and time is the average time it took that cohort to complete the study. Since the test did ask them to distinguish between near vs far collisions, it is worth looking at how often each group got the right overall direction regardless of getting the proximity correct. 

| User Category | N | Exact Accuracy % | Approx. Accuracy (%) | Time (s) |
|---------------|---|------------------|----------------------|----------|
| Novice | 3 | 27 | 58 | 56.2 |
| Expert | 2 | 77 | 88 | 67.1 |
| **All**| **5** | **47** | **70** | **60.6** |

From these results, one can see that while the "expert" users (the designers) enjoyed a higher accuracy overall in interpreting cues, this did come at a cost of taking longer to complete the study task. We also received some feedback from the novice users that they would forget the mapping between near and far in vibration intensity, hence the look at accuracy at direction (front left) vs exact proximity condition (near or far). Since relaxing proximity nearly doubled accuracy scores for the novices, clearing up that confusion could raise the floor from which any subsequent experience with the device starts.

Additionally, from the confusion matrix of all users, one can see there was also some confusion about the direct lateral cues, since they were formed by a combination of front and rear motors vibrating simultaneously. This confusion accounts for 13.75% of responses in the general case and 16.7% of the novice case.

<div style="text-align: center">
<img src="{{ '/assets/img/hive_mind/hive_mind_confusion.png' | relative_url }}" alt="confusion" style="width:100%;">
</div>

We also received some subjective feedback about the dimensions of the device, namely that it was a little on the large side, considering the frontal cues worked best if your fingers were directly over the motors. Overall, it was concluded that the design would need to be iterated upon. 

The other core functionality being assessed was if the tilt commands and knob were intuitive. For this secondary assessment, my project partner built a ROS2 (Foxy Fitzroy) simulation (Webots) to simulate 3 crazyflie drones operating at a fixed altitude after takeoff.  

<div style="text-align: center;">
<img src="{{ '/assets/img/hive_mind/hive_mind_evaluation_ros.png' | relative_url }}" alt="ros sim" style="width: 75%;"/>
</div>

This test was more warmly received, with users describing it as fun though challenging. Launch proved particularly challenging since the controller immediately started issuing commands to the drone, leading to a lot of crashes during takeoff. We determined this could be patched in the short-term by adding a delay to when the controller starts issuing commands in future simulations. Long-term a switch or button could be added that toggles if the controller is active or not.

### Future Work
While I am no longer working on this project,
based on feedback, there are some directions that I would pursue in future iterations of this system. First, reducing the width and height would improve user comfort and would be simple to do. 

Another thing that could help would be a just noticeable difference (JND) study to help make cues more distinguishable from one another. In this study, the goal would be to determine the smallest changes in motor actuation that a user could perceive. My belief is that such a study could improve distinction between lateral and frontal/rear cues in particular, offering room to improve accuracy for non-expert users. Additionally, the limited data that we do have suggests that eliminating some of the sources of existing confusion could be achieved through better and longer coaching.

However, just because some confusion can be eliminated through coaching, doesn't mean that's the best solution path forward.  If we can reduce any confusion imposed via crosstalk, that saves time on training and improves the user experience through the training process and beyond. The clearest path to accomplish this would be better separating the motors mechanically.

The catch is that this would likely involve relaxing the 'device you can pick up' constraint. One possible design under consideration would place motors onto thimbles connected by retractable reels in the main body of the controller. 

The relaxation of the 'pick up and go' constraint appears to be the direction the lab's principal investigator and a collaborator went in their related work. They ditched the PLA box in favor of a vibrotactile glove, which was also more common in the prior art.

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

**Principal Investigator Published Related Work as**
N. C. Schneider, J. M. Anderson, M. A. Schoen, K. K. Leang and E. Battaglia, "Flying Blind: In-Ground Effect Enabled Haptic Teleoperation of Uncrewed Aerial Vehicles," 2026 IEEE Haptics Symposium (HAPTICS), Reno, NV, USA, 2026, pp. 1-7, doi: 10.1109/HAPTICS66823.2026.11495453.