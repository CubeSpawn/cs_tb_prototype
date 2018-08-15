# cs_tb_prototype
Turning TurtleBot3 into CubeSpawn

This is a preliminary prototype of the simulation environment hacked out of the very nicely built TurtleBot3 packages over at https://github.com/ROBOTIS-GIT

Before installing this I'd suggest installing ROS kinetic as described here: http://emanual.robotis.com/docs/en/platform/turtlebot3/pc_setup/
or the full official install here: http://wiki.ros.org/kinetic/Installation/Ubuntu

Note I'm running on Ubuntu LTS 16.04 with ROS Kinetic if you run on a different platform, godspeed and best-o-luck, I dunno about that.

The nice thing about the ROBOTIS instructions is they cover several configuration issues as well as the mechanics of the install 

All credit to them for skillfully providing the first step!

This is parts of 3 packages, which it is hoped can be folded into a single metapackage for CubeSpawn
I left it intact to the degree there is a Turtlebot 3 still in it for now, until I master the concepts of feeding signals from a keyboard or other sources for dynamic interaction with the Cube centric robots.

Since this was 3 folders, it still is, meaning you'll need to copy the folders from the cloned folder up one level
i.e. 
$ cd ~/catkin_ws/src
$ git clone https://github.com/CubeSpawn/cs_tb_proto.git
cd cs_tb_proto
mv * ..
cd ..
rm -fdr cs_tb_proto
This also nukes the hidden .git folder, but you don't need it, unless you need it for something, but I dunno what, my dev env and this are seperated.

if you install the ROBOTIS script mentioned above it adda a bunch of aliases to your ~/.bashrc
allowing you to type a bunch of 2 letter commands to do things like sb instead of "source ~/.bashrc"
and cm instead of "cd ~/catkin_ws && catkin_make"... you get the idea!

these folders were copied from a live install

they where at ~/catkin_ws/src/

to compile any changes
$ ~catkin_ws/src$ cd ~/catkin_ws && catkin_make (or, if you installed the ROBOTIS above, the alias "cm")

to run:

Terminal 1
$ roscore

Terminal 2
$ roslaunch cs_turtlebot3_gazebo turtlebot3_world.launch

Terminal 3
$ roslaunch cs_turtlebot3_gazebo turtlebot3_gazebo_rviz.launch

Terminal 4
$ roslaunch cs_turtlebot3_teleop cs_turtlebot3_teleop_key.launch
