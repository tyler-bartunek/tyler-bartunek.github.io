---
layout: default
---

## Welcome!
My name is Tyler Bartunek, and I'm a mechanical engineer with two degrees in the subject, both with a robotics/automation flavor to them. I've worked as a researcher, teaching assistant, and tutor within the University of Utah's department of mechanical engineering, with the latter two experiences spanning a good breadth of the material one would cover during an undergraduate degree. 

The purpose of this site is to feature selected work from my academic, professional, and project work. Show off a little.

But most prominent among all work presented will be the project work with the ShoeBot, a novel open-source platform under ongoing development by yours truly. We're talking full stack hardware and software development, from actuator sizing to ROS architecture.

## More on the ShoeBot
Picture this: a framework that allows you to use a 3D printer and raspberry pi to take a leftover shoebox and upcycle it into a mobile robot.

With me so far? Did you picture your mobile robot having wheels or legs? Under the ShoeBot system, it doesn't matter. You can freely switch between the two, provided you have the right modules printed out.

A standardized 3D-printable rail mounting system allows for the creation of completely reconfigurable mobile robots, with pre-designed modules intended to be buildable with nothing more than a 3D printer, screwdriver, and a soldering iron. The documentation and associated files for this project are hosted on a github repository with associated wiki, both of which are linked below.

Additional custom hardware files are included for a wiring harness for the SPI bus connections that employs a 74HC595 shift register to reduce the number of CS lines. While the ROS code under development assumes this board is present at the heart of the ShoeBot architecture, you are free to develop your own equivalent or modify the spi_driver code to suit your purposes.

The guiding philosophy is that if you have a box, soldering iron, basic fasteners, and a 3D printer then you should be able to put this system together. Now, at 
present it will fall slightly short of this noble goal, but efforts will be made to get back in alignment.

[Link to the repository](https://www.github.com/tyler-bartunek/ShoeBot/)

[Link to the wiki](https://www.github.com/tyler-bartunek/ShoeBot/wiki)


