**Goal**: Record data published on a topic and a service so you can replay and examine it any time.

## BACKGROUND
`ros2 bag` is a command line tool for recording data published on topics and services in your ROS 2 system.
It accumulate the data passed on any number of topics and services, and **save it in database**

## Managing Topic Data
### 1 Setup
`ros2 run turtlesim turtlesim_node`
`ros2 run turtlesim turtle_teleop_key`

Let's also make a new dir to store our saved recordings,just as good practice
`mkdir bag_files`
`cd bag_files`

### 2 Choose a topic
`ros2 bag` can record data from messages published to topics. 
`ros2 topic list`

choose `/turtle1/cmd_vel`

echo to terminal
`ros2 topic echo /turtle1/cmd_vel`

### 3 Record topics
`ros2 bag record <topic_name>`
Move to bag_files which we have created before

**Record multiple topics**
You can also record multiple topics, as well as change the name of the file `ros2 bag` saves to

`ros2 bag record -o subset /turtle1/cmd_vel /turtle1/pose`
subset is the file name

### 4 Inspect topic data
`ros2 bag info <bag_file_name>`

### 5 Play topic data
Before replaying the bag file, enter Ctrl C in the terminal where the teleop is running

`ros2 bag play subset`
















