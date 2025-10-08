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

## ros2 topic list
