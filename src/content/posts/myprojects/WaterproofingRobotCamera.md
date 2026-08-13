---
title: "Eyes for a Swimming Robot"
date: 2026-05-08T16:29:56-04:00
draft: true
searchHidden: true
ShowToc: true
author: Clayton Easley
tags: 
    - Robotics
    - Linux
    - ROS1
    - IEEE
    - Raspberry Pi Zero PoE
    - Waterproofing
    - MATE ROV
    - Docker
description: How my robotics team and I worked together to design waterproof PoE cameras using a Raspberry Pi Zero
categories: ["Robotics", "Electronics"]

weight: 1

cover:
    image:

editPost:
    URL: https://github.com/clayton14/MySite2.0
    Text: "Suggest Changes"
---


# Introduction

During my Freshman year (2023 to 2024), I joined my previous university's IEEE club, which hosts several student projects. 
One of the most ambitious projects was the underwater robotics team, which participates each year in the [MATE ROVs Explorer Class](https://materovcompetition.org/explorer).
Although we all worked together, my task was to develop 3 waterproof networked camera modules for the pilot.
With the clock already ticking, I had to quickly get the subsystem working with the robot in time for the competition.
I will be sharing my design, along with the challenges I faced and how I overcame them using the resources I had available.



### About the compition

The best way I can describe [the MATE ROV compition](https://materovcompetition.org/) is like [FRC](https://firstroboticscanada.org/frc/) but... in a pool. Diffrent robotics teams work together to build a [remotely operated underwater vehicle](https://en.wikipedia.org/wiki/Remotely_operated_underwater_vehicle), *hence the name ROV*, and compleat a set of diffrent tasks for points. 
Due to the fact that we are submerged at least 10 feet in a pool, waterproofing is a forefront challenge. On top of this, the ROV pilot can't directly look into the water without penality. This makes having a relable video stream with as little latency to the pilot critical. Without it you may as well be blindfolded. 



# Physical Design
---
Step one was coming up with a solid design for the camera module and its housing. 
If any water leaks into the electronic enclosures it’s an immediate game over. Before the housing is constructed the electronics must be suited for the task at hand. The pilot needed several different camera angles mounted around the robot to help steer the ROV and manipulate 
<a target="_blank" href="https://bluerobotics.com/store/thrusters/grippers/newton-gripper-asm-r2-rp/"> The Gripper </a>



## The Brains

For the brains of the camera I chose the [raspberry pi zero 2w](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/) for its compact form factor and ARM Cortex-A53 clocked at 1GHz. 

The pi zero also supports h.264 video compression which helps reduce the bandwidth. 
{{< figure src="/picam/pizero.webp" class="img-right" with=200 height=200  alt="raspberry-pi-zero-2-w" >}}
The high clock speed and added h.264 encoding would be more than enough for video streaming 24fps at SD to HD quality. 


The second reason the pi zero was chosen was due to it's wide adoption and Linux support. There are many, probably faster,  SBC in this formfactor our there, but I did not want to hit a dead end with unsupported distributions as [ROS](https://www.ros.org/) was a requirement Regardless, [dead ends](#battling-ros) were hit anyway.  

### The Camera 

For the cameras I used the [Raspberry Pi Zero Camera Rev 1.3](https://www.raspberrypi.com/documentation/accessories/camera.html#hardware-specification) which makes use of a [5MP OV5647 image sensor](https://docs.arducam.com/Raspberry-Pi-Camera/Native-camera/5MP-OV5647/). 
When I was was choosing a camera module I noticed that almots all the image senors on the Raspberry camera modules use [rolling shutter](https://en.wikipedia.org/wiki/Rolling_shutter) which, at the time, made me a little nervous.   

*bottleneck forshadows*

Cameras with a rolling shutter capture an image one row of pixels at a time. 

which when acclerating can cause distortion, which might make it harder for the pilot to operate. 


## Data and Power

With a camera and computer chosen I had to find a way to power and communicate with them. 
The first thing that comes to mind when I hear *power* and *data* is [Power over Ethernet](https://en.wikipedia.org/wiki/Power_over_Ethernet) (PoE) which would allow us to power the cameras with a network switch as a power supply. 
Each camera then only needs one cable for both power and data. 
The raspberrypi zero dose not have native in supprt for Ethernet or PoE, but this be sloved using a hat.  

{{< details summary="camera network toplogy" >}}

Put image here

{{< /details >}}

Knowing there I have to account for a total of three cameras I did some rough bandwidth calcuations.


### Waterproof Enclouser

{{< details summary="See Full Bill of Materials" >}}

---

PUT TABLE HERE

{{< /details >}}

<br>

If any water leeks into the electronic enclousers it's an immediate game over.
I had to come up with a design that would ensure water woulden't sneek its way in, and find a way to get power and data to the camera. 



If this enclouser was a real product it would have an [Ingress Protection code](https://en.wikipedia.org/wiki/IP_code) of at least **IP68**. The second digit in the code indicates how well the enclouser prevents the ingress of water, and at the level of **8** requires full submersion in water at a depth of 1 meater (~3.2ft).   

<!-- {{< gallery >}} -->
<!-- {{< wfigure src="/notes/audicty_wav_encoding_settings.webp" align="left" width="300px" >}} -->
<!---->
<!-- {{< wfigure src="/notes/audicty_wav_encoding_settings.webp" align="right" width="300px" >}} -->
<!-- {{< /gallery >}} -->


Students from prevoius compitions used a waterproof project box with a clear lid that housed a Raspberry PI Camera setup. But, with a new ROV frame, and needing to mount the camera on [the gripper](https://bluerobotics.com/store/thrusters/grippers/newton-gripper-asm-r2-rp/) we needed something more compact. [The Raspberry Pi Zero 2 W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/) was the best contender, as it is far more compact and fit withen our budgett and timeline (more on this later). 

The next task was getting power and data transfer to each of the three pi's.


Now, I do have to preface that this idea was inspired by another robotics teams design, but with major changes. I unforunatlly do not remember what team I had spoken to about there design, but I do remember that they were also using a PI zero in there design.

# Software

## Battling ROS

## FFmpeg

# Other Chalanges

Before I go over the design and implemtation it's important to understand the scope of the project, and the constrantes both I, and the team faced. 







