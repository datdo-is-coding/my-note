#beginner #rqt #rqt_graph #topics
**Goal**: use rqt_graph and command line tools to introsopect ROS 2 topics

**BACKGROUND** : **topics** are vital element of the ROS graph that act as a bus for nodes to exchanges messages.
A node may publish data to any number of topics and simultaneously and have subscriptions to any number of topics

## TASKS
### 1. run rqt_graph
We first run  `ros2 run turtlesim turtlesim_node`
We then  run `ros2 run turtlesim turtle_teleop_key`

We open a new terminal and enter 
`ros2 run rqt_graph rqt_graph`

![[Pasted image 20251008104139.png]]
We can see from the above 2 actions and 1 topic.**turtlesim** is subscribed to **cmd_vel** and **teleop_turtle** is the publisher

## 2. ros2 topic list
`$ ros2 topic list`
`/parameter_events
`/rosout
`/turtle1/cmd_vel
`/turtle1/color_sensor
`/turtle1/pose`


`$ ros2 topic list -t`
will return the same list of topics, this time with the topic appended in brakets
`/parameter_events [rcl_interfaces/msg/ParameterEvent]
`/rosout [rcl_interfaces/msg/Log]
`/turtle1/cmd_vel [geometry_msgs/msg/Twist]
`/turtle1/color_sensor [turtlesim/msg/Color]
`/turtle1/pose [turtlesim/msg/Pose]`

## 3. ros2 topic echo

`ros2 topic echo <topic_name>` : to see that data being published on a topic.
e.g  `ros2 topic echo /turtle1/cmd_vel`

uncheck the **Debug** box

## 4. ros2 topic info
Topics don't have to only be one-to-one communication; they can be one-to-many, many-to-one, or many -to-many

`ros2 topic info /turtle1/cmd_Vel`
`Type: geometry_msgs/msg/Twist
`Publisher count: 1`
`Subscription count: 1`

## 5. ros2 interface show
Nodes send data over topics using messages. Publishers and subscribers must send and receive the same type of message to communicate.

E.g we recall that cmd_vel topic has the type `geometry_msgs/msg/Twist`
This means that in the package `geometry_msgs` there is `msg` called `Twist`

`ros2 interface show <msg_types`
E.g ` ros2 interface show geometry_msgs/msg/Twist`

    Vector3  linear
            float64 x
            float64 y
            float64 z
    Vector3  angular
            float64 x
            float64 y
            float64 z
this tells you that /turtlesim node is expecting a message with two vectors. linear and angular.

## 6. ros2 topic pub

You can publish data to a topic directly from the command line using
`$ros2 topic pub <topic_name> <msg_type> '<args>'`

The `<args>` argument is the actual data you'll pass to the topic.

There are four ways to use `pub` command.

### a. Publishing dictionary strings
In order to publish data to a topic, you pass the data in the form of YAML strings

`ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"`

You can pass only the arg you care about with this
`ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0}, angular: {z: 1.8}}"`

### b. Publishing an empty message
`$ ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist`
this will publish default values (in this case all 0s)

### c. Autocomplete

`ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist <TAB>`
TAB FURIOUSLY

### d. Using the raw autocompleted string
`\'linear:\^J\ \ x:\ 0.0\^J\ \ y:\ 0.0\^J\ \ z:\ 0.0\^Jangular:\^J\ \ x:\ 0.0\^J\ \ y:\ 0.0\^J\ \ z:\ 0.0\^J\'`

At times you want to publish data to your topic only once rather than continuously
`ros2 topic pub --once -w 2 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"`

`-w 2` is an optional arg wait for 2 subscribers to that topic

`Waiting for at least 2 matching subscription(s)...
`publisher: beginning loop
`publishing #1: 
`geometry_msgs.msg.Twist(linear=geometry_msgs.msg.Vector3(x=2.0, y=0.0, z=0.0), angular=geometry_msgs.msg.Vector3(x=0.0, y=0.0, z=1.8))


## 7. ros2 topic hz
You can also view the rate at which data is publishing
`ros2 topic hz /turtle1/cmd_vel`
## 8 ros2 topic bw
The bandwidth used by a topic can be viewed using:
`$ ros2 topic bw /turtle1/cmd_vel`
It returns the bandwidth utilization and number of messages being published to the /turtle1/cmd_vel
`Subscribed to [/turtle1/cmd_vel]`
`63 B/s from 2 messages`
	`Message size mean: 52 B min: 52 B max: 52 B`

## 9 ros2 topic find
To list a list of available topics of a given type use
`ros2 topic find <topic_type>`
(which is the message type)