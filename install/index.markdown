---
author: admin
comments: false
date: 2013-11-19 20:43:44+00:00
layout: page
slug: install
title: Install
wordpress_id: 24
---

[no_toc]
**_MoveIt! is currently developed and works against Ubuntu and ROS Indigo and Hydro. It is recommended that you move to ROS Indigo for the latest features. MoveIt! for ROS Groovy is no longer actively supported.
_**

_Note for Ubuntu 13.4 32 bit users_: There is a bug with GCC 4.7 on Ubuntu 13.4 32bit with Eigen 3.1.2. It's not likely to be fixed, so upgrade/downgrade your system to 13.4 64 bit resp. 12.4.

_If you are a developer_: please scroll down for instructions on installing from source. Most users should be able to use just the binary instructions.



* * *





# Binary Installation Instructions (for users)




#### STEP 0: Install ROS


Follow all the instructions to install the base version of ROS: [Install ROS-Base](http://wiki.ros.org/indigo/Installation/Ubuntu). Please make sure you have followed all the ROS installation steps, including calls to rosdep.

MoveIt! can be installed directly as a set of debian packages on Ubuntu. To get a complete installation, choose your ROS distribution below:

** ROS Hydro **

[toggle title="ROS Hydro Installation Instructions"]


#### STEP 1: Ubuntu Installation: Debian Packages for MoveIt!


[sourcecode language="bash" gutter="false" highlight="1"]
sudo apt-get install ros-hydro-moveit-full
[/sourcecode]


#### STEP 2: Debian Packages for MoveIt! with the PR2


If you would like to use MoveIt! with the PR2 with ROS Hydro (recommended if you are following the tutorials on the MoveIt! wiki):

[sourcecode language="bash" gutter="false" highlight="1"]
sudo apt-get install ros-hydro-moveit-full-pr2
[/sourcecode]


#### STEP 3: Setup your environment


[sourcecode language="bash" gutter="false" highlight="1"]
source /opt/ros/hydro/setup.bash
[/sourcecode]

[/toggle]

**ROS Indigo **

[toggle title="ROS Indigo Installation Instructions"]


#### STEP 1: Ubuntu Installation: Debian Packages for MoveIt!


[sourcecode language="bash" gutter="false" highlight="1"]
sudo apt-get install ros-indigo-moveit-full
[/sourcecode]


#### STEP 2: Debian Packages for MoveIt! with the PR2


These are not yet fully available for the PR2.


#### STEP 3: Setup your environment


[sourcecode language="bash" gutter="false" highlight="1"]
source /opt/ros/indigo/setup.bash
[/sourcecode]

[/toggle]



* * *





# Source Installation Instructions (for developers)




#### STEP 0: Install ROS


Follow all the instructions to install the base version of ROS: [Install ROS-Base](http://www.ros.org/wiki/hydro/Installation/Ubuntu). Please make sure you have followed all the ROS installation steps, including calls to rosdep.


#### STEP 1: Get the wstool package


[sourcecode language="bash" gutter="false" highlight="1"]
sudo apt-get install python-wstool
[/sourcecode]

Now follow the steps for your particular ROS version.

** STEP 2 & 3: ROS Hydro **
[toggle title="ROS Hydro Instructions"]


#### STEP 2: Download the source code


[sourcecode language="bash" gutter="false" highlight="1,2,3,4,5,6,7,8,9"]
source /opt/ros/hydro/setup.bash
mkdir moveit
cd moveit
mkdir src
cd src/
wstool init .
wstool merge https://raw.github.com/ros-planning/moveit_docs/hydro-devel/moveit.rosinstall
wstool update
cd ..
[/sourcecode]


#### STEP 3: Make sure MoveIt! dependencies are installed


[sourcecode language="bash" gutter="false" highlight="1"]
rosdep install --from-paths src --ignore-src --rosdistro hydro -y
[/sourcecode]

[/toggle]

** STEP 2 & 3: ROS Indigo **
[toggle title="ROS Indigo Instructions"]


#### STEP 2: Download the source code


[sourcecode language="bash" gutter="false" highlight="1,2,3,4,5,6,7,8,9"]
source /opt/ros/indigo/setup.bash
mkdir moveit
cd moveit
mkdir src
cd src/
wstool init .
wstool merge https://raw.github.com/ros-planning/moveit_docs/indigo-devel/moveit.rosinstall
wstool update
cd ..
[/sourcecode]


#### STEP 3: Make sure MoveIt! dependencies are installed


[sourcecode language="bash" gutter="false" highlight="1"]
rosdep install --from-paths src --ignore-src --rosdistro indigo -y
[/sourcecode]

[/toggle]


#### STEP 4: Build MoveIt!


Assuming you are in the moveit folder created above,

[sourcecode language="bash" gutter="false" highlight="1"]
catkin_make
[/sourcecode]


#### STEP 5: Setup your environment


You will have to do this every time you work with this particular source install of the code. Assuming you are in the moveit folder created above,

[sourcecode language="bash" gutter="false" highlight="1,2"]
source devel/setup.bash
# or .zsh, depending on your shell
[/sourcecode] 
