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
    - Waterproof
    - Waveshare
    - Raspberry Pi Zero Hats
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


# Intro

During my Freshman year (2023 to 2024) I had joined my prevoius universities IEEE club, which hostes a number of student projects.
One of the most ambitious projects was the under water robotics team which particapates each year in the [MATE ROVs Explorer Class](https://materovcompetition.org/explorer) compitition. Although we all worked together, we each had diffrent tasks, and my task was to devlop waterproof networked camera modules that we mounted around the robot.  

**MATE ROV in a Nutshell**

The best way I can describe MATE ROV is like [FRC](https://firstroboticscanada.org/frc/) but... in a pool. Diffrent robotics teams work together to build a [remotely operated underwater vehicle](https://en.wikipedia.org/wiki/Remotely_operated_underwater_vehicle), *hence the name ROV*, and compleat diffrent tasks for points. 
Due to the fact that we are submerged at least 10 feet in a pool, waterproofing is a forefront challenge. On top of this, the ROV pilot can't directly look into the water without penality. This makes having a relable video stream critical to the pilot critical, without it you may as well be blindfolded. 


In this post I will share both my camera design and the challenges I had faced. 

## Hardware and Enclouser

If any leeks there way into the electronic enclousers it's an immediate game over.  
I had to come up with a design that would ensure water woulden't sneek its way into the enclouser, and find a way to get power and data to the camera.


Now the first thing that comes to mind is [Power over Ethernet](https://en.wikipedia.org/wiki/Power_over_Ethernet) (PoE) 





Now, I do have to preface that this idea was inspired by another robotics teams design, but with major changes. I unforunatlly do not remember what team I had spoken to about there design, but I do remember that they were also using a PI zero in there design.


## Battling with ROS



# Major Chalanges

Before I go over the design and implemtation it's important to understand the scope of the project, and the constrantes both I, and the team faced. 

### Sechduling the Ordering of Components

Now, I can't be the only person to have experanced this, and prehaps may be the reson you are reading this insted of being producative. 

Soo... you just finsised the design for a new thing-a-ma-bob, and you just sent your BOM to whatever burracrat sits above you. This is because your BOM **must be approved** by said beurreacat. Now, for some reson, this **approval** takes 10 to 15 business days to review, before anything is even sent to a manafacture. This does not take into account for the time it takes for get shipped to you. 

This was a major issue for everyone on the team, simply due to the fact that we were a club at our universitie were restricted by the sechduling of *club orders* which was at most bi-weeekely. The university would collect all clubs orders and send them out as one batch order. 
Not only did this waste a lot of time but it made hardware revisions  

ROS integration 
Time Constrantes

# Design and Plan

## Machinacal Hardware

## Electrical Hardware

## Sofware Bashed Out ROS




