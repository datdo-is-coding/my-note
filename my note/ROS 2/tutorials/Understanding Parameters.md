## BACKGROUND
- Parameters are configuration values (integers,floats,boolean,strings,lists) stored per node
- Used to define node setting and can be be modified at runtime or startup
# Tasks
### ros2 param list
Too see that parameters belonging to your nodes
### ros2 param get
To display the type and current value of parameter
`ros2 param get /turtlesim background_g
`Integer value is: 86

### ros2 param set
To change a parameter's value at runtime
`ros2 param set <node_name> <parameter_name> <value>`

### ros2 param dump
`ros2 param dump <node_name>`
view all of a node's current param values 
this command output to the standard output **stdout**

`ros2 param dump /turtlesim >  turtlesim.yaml`

### ros2 param load
You can load parameters from a file to a currently running node using the command
`ros2 param load <node_name> <parameter_file>`

`ros2 param load /turtlesim turtlesim.yaml`

**NOTE** Read-only param can only be modified at startup and not afterwards

### Load parameter file on node startup
`ros2 run <package_name> <executable_name> --ros-args --params-file <file_name>`