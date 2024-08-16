
# ROS (ros)

A Robot Operating System (ROS) Version 1 Noetic DevContainer

1. Open a terminal and type roscore
2. Open a second terminal and type `rosrun turtlesim turtlesim_node`
3. Open a third terminal and type `rostopic pub /turtle1/cmd_vel geometry_msgs/Twist` (continue with tab) to change in this case the velocity of our turtle. Type `rostopic pub /turtle1` (and tab) to see other things you can do.

All the moves of the turtle are available on http://localhost:6080/