# cs_tb_prototype
Turning TurtleBot3 into CubeSpawn

This is a preliminary prototype of the simulation environment hacked out of the very nicely built TurtleBot3 packages over at https://github.com/ROBOTIS-GIT

Before installing this I'd suggest installing ROS kinetic as described here: http://emanual.robotis.com/docs/en/platform/turtlebot3/pc_setup

or the full official install, here: http://wiki.ros.org/kinetic/Installation/Ubuntu Note: if you do this, I'd suggest still adding the robotis install up to the point of cloning thier packages. so that no core resources are missing.
or the full official install, here: http://wiki.ros.org/kinetic/Installation/Ubuntu


Note I'm running on Ubuntu LTS 16.04 with ROS Kinetic. If you run on a different platform, godspeed and best-o-luck, I dunno about that.

The nice thing about the ROBOTIS instructions is they cover several configuration issues as well as the mechanics of the install 

All credit to them for skillfully providing this first step!

This is parts of 3 tb packages, which it is hoped can be folded into a single metapackage for CubeSpawn
I left it intact to the degree there is a Turtlebot 3 still in it for now, until I master the concepts of feeding signals from a keyboard or other sources for dynamic interaction with the CubeSpawn centric robots.

after getting your ROS install in place with the instruction above.

clone the CubeSpawn test packages: 

$ cd ~/catkin_ws/src

$ git clone https://github.com/CubeSpawn/cs_tb_prototype.git

Since this was 3 folders, it still is, meaning you'll need to copy the folders from the cloned folder up one level

All the steps to do this have been encapsulated into a (primitive) shell scrip

its assumed you are still at ~/catkin_ws/src

$ cd ~/catkin_ws/src/cs_tb_prototype

$ ./setup.sh

if you install the ROBOTIS script mentioned above it adds a bunch of aliases to your ~/.bashrc
allowing you to type a bunch of 2 letter commands to do things 

like 'sb' instead of "source ~/.bashrc" (NOTE this is needed EACH time you open a new terminal)

and 'cm' instead of "cd ~/catkin_ws && catkin_make"... you get the idea!

these folders were copied from a live install

they were at ~/catkin_ws/src/

to compile any changes
$ ~catkin_ws/src$ cd ~/catkin_ws && catkin_make (or, if you installed from the ROBOTIS instructions above, the alias "cm")

There is also a test environment for just Gazebo consisting of 2 world files
in a terminal. cd to: ~/catkin/ws/src/cs_array/world
and run
$ gazebo test.world 
or
$ gazebo cs_array.world

These are both static models, but you can tweak setting and save them, getting insight into the XML for various settings and controls.

To run the actual robot environment:

Terminal 1
$ roscore

Terminal 2
$ roslaunch cs_turtlebot3_gazebo turtlebot3_world.launch

Terminal 3
$ roslaunch cs_turtlebot3_gazebo turtlebot3_gazebo_rviz.launch

Terminal 4
$ roslaunch cs_turtlebot3_teleop cs_turtlebot3_teleop_key.launch

I have the install duplicated on 4 machines on the same network segment and use a software KVM (synergy) to map the desktops into one work environment, this allows for running each terminal on its own screen.


footnotes:

the following was collapsed into the "setup.sh" mentioned above
##################################################################################################
i.e. 

cd cs_tb_prototype

mv * ..

cd ..

rm -fdr cs_tb_prototype

This also nukes the hidden .git folder, but you don't need it, (unless you need it! for something else, but I dunno what!), my dev env and this are seperated.
##################################################################################################

