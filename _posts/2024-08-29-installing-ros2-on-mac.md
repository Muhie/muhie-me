---
layout: post
title:  "Installing ROS2 on an ARM based Macbook 2024"
date:   2024-08-29 11:15:45 +0100
categories: jekyll update
---

## My ideal ROS2 Development Environment

For me, the ideal ROS2 environment consists of the following packages/software:
1. Operating system: Ubuntu
2. Code editor: Visual Studio Code
3. The default ROS packages: (Rviz, Gazebo, ect.)

These packages are the bear minium to create projects using ROS2 in my opinion

## Creating My Environment

I downloaded the Ubuntu dailiy ARM64 build from here: add link. Then using UTM (an open source virtual machine package), I installed Ubuntu in the usual fashion. One thing to note is that you have to make sure that you change the boot device on UTM so it does not boot back into the ISO after installing Ubuntu.

## Downloading ROS

This was a breeze using the instructions on their website. No issues to report here.

## Downloading Gazebo
This is where I ran into some issues - due to the openGL 4.1 version on my Ubuntu VM. After downloading Gazebo I was unable to start the simulator; I had tried changing my drivers and other troubleshooting steps, after lots of googling I stubbled accross a github post from the author: PSandro who detailed a flag to enable XWAYLAND rendering. After entering this command: 
```env -u WAYLAND_DISPLAY gz sim -v 4 <YOUR FILE NAME HERE.sdf> --render-engine ogre``` gazebo ran perfectly!

I hope that this helps anyone stuggling to install ROS2 on macos