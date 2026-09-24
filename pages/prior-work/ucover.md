---
layout: default
---

## Motion-Capture-Based Ergonomics Analysis of Containment Hood 

<figure style="text-align: center;">
<img src="{{ '/assets/img/ucover/mocap_image.png' | relative_url}}" alt="Visual Abstract" style="width: 75%;">
<figcaption style="font-size: 0.85em; color: #666;">Screenshot of the motion capture (Motive, Optitrack) data from an anonymous particpant performing an intubation with the aerosol contaiment hood in place.</figcaption>
</figure>

<strong>Outcomes: </strong> 
- Developed python code that auto-assigns motion capture data with a RULA score (ergonomic measure).
- Motion capture data revealed no meaningful ergonomic difference between using a protective hood over a simulated patient vs not having that hood in place.
- Peer-reviewed publication in [Ergonomics in Design](https://journals.sagepub.com/doi/abs/10.1177/10648046261429139). <br>

<strong>Status: </strong> All data collected and equipment returned to the University Center for Medical Innovation as of early 2024. 

<strong>Skills: </strong> Motion Capture, Python, MATLAB, Data Analysis, Cross-Disciplinary Collaboration

### Overview
In the wake of the global pandemic, an important question for many research teams was how to better protect medical personnel from patient aerosols including airborne pathogens. Researchers at the University of Utah began developing the U-COVER (referred to from this point forward as 'the hood'), a portable containment device designed to provide such protection. The aim of the study was to assess the user experience with this hood, from ergonomics to how users felt about using it. Subjective measures were captured with surveys such as the NASA task load index (TLX) and the system usability survey (SUS). 

My responsibilities involved co-executing the data collection sessions and processing the resulting data. This latter responsibility meant co-authoring scripts for converting motion capture data into per-frame RULA scores, as well as creating a visual of endotracheal tube motion relative to the hood across both the "hood" and "no-hood" conditions. 

### Data Collection
Individuals with medical training commensurate with performing a routine intubation procedure were recruited to participate in the study with help from our partners at the University of Utah School of Medicine and Center for Medical Innovation (CMI). Participants were tasked with intubating a training mannequin multiple times per hood condition ("hood" vs "no-hood").

Motion data was captured with an OptiTrack infrared tracking system and reflective markers placed on them and the equipment they were using during the procedure. For user movement, we used an existing upper body marker set in the Motive software. Custom static object marker sets were used for medical equipment such as the bed, head of the mannequin, endotracheal tube, laryngoscope, Ambu bag, as well as the actual hood itself.

As we (myself and my colleague also working on this project) gained familiarity with the experimental setup and gap-filling capabilities of the software, my colleague recommended changes to the marker sets to facilitate higher-fidelity data captures. I assisted with implementing these changes, designing caps to place on the laryngoscope and endotracheal tube stylets to provide flat surfaces for the markers to adhere to. 

The TLX was filled out after both conditions and the SUS only after the "hood" condition. 

### Post-Processing

Marker data for the users were exported and fed through a pre-existing data pipeline in V3D for extracting joint angle measurements. Alongside my aforementioned colleague, we developed a script for converting these angle measurements into RULA scores, with my contributions primarily being in the realm of encapsulating a lot of the user-level data processing operations into a Python class for batch processing. That script/class was also extended later to extract per-phase-of-intubation-specific ergonomics and/or joint data. 

I also helped developed code that would map the raw marker data for the endotracheal tube and hood from the global coordinates during its respective capture session into a coordinate space that was relative to the corner of the bedframe. This way, we would have an apples-to-apples comparison for how the tooling moved when constrained by the hood vs unconstrained motion.

### Conclusion
We (the authors of the study) were unable to find a clinically meaningful difference in the time to complete the procedure, ergonomics during the procedure, or the perceived mental workload by the user. More details can be found in the publication in Ergonomics in Design.

As a researcher, it was a great project highlighting the importance of collaboration as well as reinforcing my data analysis and script-writing skills. 

### Published in
[Ergonomics in Design](https://journals.sagepub.com/doi/abs/10.1177/10648046261429139)