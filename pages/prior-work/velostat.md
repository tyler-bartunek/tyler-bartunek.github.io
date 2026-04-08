---
layout: default
---

## Velostat Force Sensing

<figure style="text-align: center;">
<img src="{{ '/assets/img/velostat/velostat_abstract.png' | relative_url}}" alt="Visual Abstract" style="width: 75%;">
<figcaption style="font-size: 0.85em; color: #666;">I constructed a number of inexpensive force sensors and evaluated them under static, cyclic, and fingertip-based loading.</figcaption>>
</figure>

### Overview
My main research as a member of the human-centered haptics and robotics (h-CHAR) lab, was focused on creating inexpensive tactile sensors using a material called Velostat (3M). These tactile sensors were to be used in a system being developed under an NSF grant to "telementor" individuals to perform medical procedures [1].

Over the course of this project, I constructed sensors using a hole punch for repeatable Velostat dimensions as well as conductive thread, tape, cling wrap, and JST crimp-on connectors. I also improved the mechanical design and sampling rate of a custom compressive testing setup in the lab. 

<div style="text-align: center;">
<img src="{{ '/assets/img/velostat/velostat_assembly_photos.png' | relative_url}}" alt="Assembly" style="width: 75%;">
</div>

### Research Questions
This material has been used to some success in similar sensing setups, with some notable examples provided in the "related work" section [2-4]. However, in the prior art it has been noted that sensors constructed using this material exhibit reliability, hysteresis, and accuracy problems. The scope of this project was to investigate if:

1. layering the material within the sensor improves performance, and
2. if it does, is there a point of diminishing returns where adding layers does not boost performance?

We found that the answer to the first question was yes, and the answer to the second question was after 3-4 layers there were no meaningful benefits. As a point of comparison, data was also collected for a commercially-available FSR 402 sensor from Interlink Electronics.

### Data Collection
All data was collected using a custom C++ script that read the serial byte stream from an Arduino Uno and ADS1220 24-bit analog-to-digital converter. The ADC was connected to a 5 kg load cell, which was calibrated using a set of masses. With this setup, we were able to obtain reliable force measurements as small as 0.1 N, as verified with an ATI force/torque sensor. 

<div style="text-align: center;">
<img src="{{ '/assets/img/velostat/velostat_load_cell_volt_divide.png' | relative_url}}" alt="load cell and volt divider" style="width: 75%;">
</div>

The Velostat sensors were connected to the Arduino in a voltage divider configuration, as was common in the prior art.

Three flavors of evaluation were done: 
1. Static weight
2. Cyclic loading
3. User testing

That last evaluation was simply recruiting participants to press on the sensor with the finger, trying to go from 0-10 N and back down again three times at a self-directed but controlled pace. More of the design work on my end corresponded to the first two test conditions.

### Compressive Testing Mechanism
For preliminary study of Velostat, an undergraduate researcher had developed a custom compressive testing mechanism. A majority of this design was very solid and fit their tests nearly perfectly. However, as I began to build my own tests and pipeline, it became apparent that the occasional issues with reliability/stiction (not quantified, just know it sometimes wouldn't start correctly) as well as the data rate needed to be improved. Additionally, there was interest for other studies in the lab at the time to collect both loading and end-effector displacement data, where their design collected only loading data.

My redesign is shown below, as well as a breakdown immediately following it.

<!--TODO: add redesign image -->
<div style="text-align: center;">
<img src="{{ '/assets/img/velostat/velostat_indenter.png' | relative-url}}" alt="compressive redesign" style="width: 75%;">
</div>

I made a decision to keep the parts of the design that were working fairly well, but instead focused on solving four problems:

1. Flexing in the base: solved by adding some 3D-printed beams
2. Reliability/stiction: solved by replacing the actuation mechanism with a lead-screw design.
3. Data rate: solved by replacing their ADC with one that supports higher throughput.
4. No displacement measurement: added two features, an optical distance sensor and the new actuator had a built-in encoder. 

Notice that my fix for the second issue solved more than just that issue, it also contributed to the lack of displacement measurement. Beyond that though, having the open screw also improved maintainability of the system, as it allowed easy access to lubricate the motion components as necessary.

### Published as

[MDPI sensors](https://www.mdpi.com/1424-8220/25/10/3245)<br>
[Thesis (ProQuest)](https://www.proquest.com/openview/b717fe760f838be9e6eff8ef84b56520/)

### Related Work/Citations
1. Reyes, L.R.; Gavino, P.; Zheng, Y.; Boehm, J.; Yeatman, M.; Hegde, S.; Park, C.; Battaglia, E.; Fey, A.M. Towards telementoring for needle insertion: Effects of haptic and visual feedback on mentor perception of trainee forces. In Proceedings of the 2022 IEEE Haptics Symposium (HAPTICS), Santa Barbara, CA, USA, 21–24 March 2022; pp. 1–7.
2. Sundaram, S.; Kellnhofer, P.; Li, Y.; Zhu, J.Y.; Torralba, A.; Matusik, W. Learning the signatures of the human grasp using a scalable tactile glove. _Nature_ 2019, _569_, 698–702.
3. Liu, H.; Xie, X.; Millar, M.; Edmonds, M.; Gao, F.; Zhu, Y.; Santos, V.J.; Rothrock, B.; Zhu, S.C. A glove-based system for studying hand-object manipulation via joint pose and force sensing. In Proceedings of the 2017 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), Vancouver, BC, Canada, 24–28 September 2017; pp. 6617–6624.
4. Zhang, Y.; Zeng, J.; Wang, Y.; Jiang, G. Flexible Three-Dimensional Force Tactile Sensor Based on Velostat Piezoresistive Films. _Micromachines_ 2024, 15, 486.