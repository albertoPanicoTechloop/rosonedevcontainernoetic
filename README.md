
# ROS (ros)

A Robot Operating System (ROS) Version 1 Noetic DevContainer

1. Open a terminal and type `roscore`
2. Open a second terminal and type `rosrun turtlesim turtlesim_node`
3. Open a third terminal and type `rostopic pub /turtle1/cmd_vel geometry_msgs/Twist` (continue with tab) to change in this case the velocity of our turtle. Type `rostopic pub /turtle1` (and tab) to see other things you can do.

All the moves of the turtle are available on http://localhost:6080/


---------------------------------

Now we need to import the vinya_st4030_gui into src folder as a package (you need only to drag and drop, the creation of the package will be done after the catkin_make command). \
Create a robot package with `catkin_create_pkg robot` command, into this package create a folder named "msg" and in this folder the file "canread.msg" with "string msg" as text. \
After this, we need to adjust the cmake files: \
  -  robot/CMakeLists.txt \
      - find_package(catkin REQUIRED
        rospy
        std_msgs
        message_generation
        ) \
       - add_message_files(
         FILES
         canread.msg
         ) \
       - generate_messages(
         DEPENDENCIES
         std_msgs  # Or other packages containing msgs
         ) \
       - catkin_package(
          CATKIN_DEPENDS rospy std_msgs #other_catkin_pkg 
          ) \


  - vinya_st4030_gui/CMakeList\
        -  find_package(catkin REQUIRED COMPONENTS
            rospy
            std_msgs
            std_msgs
            robot
            message_generation
            #hym_msgs
            )\
        -  generate_messages(
           DEPENDENCIES
           std_msgs
           )\
        - catkin_package(
           CATKIN_DEPENDS rospy std_msgs #hym_msgs
            )\
         - catkin_install_python(PROGRAMS
            scripts/app.py
             DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
           )\

    - robot/package.xml and vinya_st_4030_gui/package.xml\
         - <build_depend>message_generation</build_depend>  //Add the following lines only to robot/package.xml\
           <exec_depend>message_runtime</exec_depend>      //Add the following lines only to robot/package.xml\
            <buildtool_depend>catkin</buildtool_depend>\
            <build_depend>roscpp</build_depend>\
            <build_depend>rospy</build_depend>\
            <build_depend>std_msgs</build_depend>\
            <build_export_depend>roscpp</build_export_depend>\
            <build_export_depend>rospy</build_export_depend>\
            <build_export_depend>std_msgs</build_export_depend>\
            <exec_depend>roscpp</exec_depend>\
            <exec_depend>rospy</exec_depend>\
            <exec_depend>std_msgs</exec_depend>\


now type: `cd /rosonedevcontainernoetic/catkin_ws`\
`source devel/setup.bash`\
`catkin_make`\

almost finished, just few commands:\
open a terminal and type `roscore`\
open a new terminal, type `cd /rosonedevcontainernoetic/catkin_ws/src/vinya_st4030_gui/scripts`\
`pip install -r requirements.txt` (maybe pip is not installed, type: `sudo apt update` and ` sudo apt install python3-venv python3-pip`)\
now again `cd /rosonedevcontainernoetic/catkin_ws` and `source devel/setup.bash`\
final command: `rosrun vinya_st4030_gui app.py` (if not, open manually a port 5000 on "ports tab" in vscode and then go in localhost:5000).

























    
