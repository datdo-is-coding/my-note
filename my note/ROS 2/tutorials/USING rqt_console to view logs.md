#beginner #rqt 


## BACKGROUND
`rqt_console` is a GUI tool used to introspect log messages in ROS2. You can collect messages over time, view them closely and in a more organized manner, filter them, save them and even reload the saved files to introspect at a different time.

## TASKS
### 1 Setup
Start `rqt_console` in a new terminal with the following command
`ros2 run rqt_console rqt_console`

![[Pasted image 20251015122002.png]]
The first section of the console is where log messages from your system will display

In the middle you have the option to filter message by excluding severity filter. You can also add more exclusion filters using the plus-sign button to the right.

The bottom section is for highlighting messages that include a string you input. You can all more filters to this section as well

## 2 Messages on rqt_consoole
`ros2 topic pub -r 1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 0.0}}"`
You will see the message

### 3 Logger levels
ROS 2'logger levels are ordered by severiy:
1. Fatal : messages indicate the system is going to terminate to try to protect itself
2. Error: messages indicate significant issues that won't necessarily damage the system, but are preventing it from functioning properly
3. Warn: issues that dont harm functionality outright
4. Info : indicate event and status updates
5. Debug: messages detail the entire step-by-step process of the system execution
The default level is **Info**. You will only see messages of the default security level and more severe levels

**SET THE DEFAULT LOGGER LEVEL**
`ros2 run turtlesim turtlesim_node --ros-args --log-level WARN`



