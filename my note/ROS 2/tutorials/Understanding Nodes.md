#nodes #beginner
## Background
The **ROS 2** graph :
![[Pasted image 20251005105728.png]]
Each node in **ROS** should be responsible for a single, modular purpose, e.g. controlling the wheel motors or publishing the sensor data form a laser range-finder. Each node can send and receive data from other nodes via topics, services, actions or parameters. 
A full robotic system is comprised of many nodes working in concert. In **ROS 2** , a single executable can contain one or more nodes.

## Tasks
### 1 ros2 run
the command launches an executable from a package.

`ros 2 run <package_name> <executable_name`

To run turtlesim, open a new terminal, and enter the following command

`ros 2 run turtlesim turtlesim_node`

<package_name> : turlesim
<executable_name> : turtlesim_node
### 2 ros2 node list
show the names of all running nodes. This is useful when you want to interact with a node, or when you have a system running many nodes and need to keep track of them
`ros2 node list`

Open new terminal and start the teleop node
`ros2 run turtlesim turtle_teleop_key`

#### 2.1 Remapping
allows you to reassign node properties: node name,topic names,services names, etc., to custom value.


Reassign the name of `/turtlesim`
`ros2 run turtlesim turtlesim_node --ros-args --remap __node :=my_turtle`

### 3 ros2 node info
`ros2 node info <node_name>`
e.g : `ros node info /my_turtle`
this command return returns a list of subscribers, publishers, services, and actions

















