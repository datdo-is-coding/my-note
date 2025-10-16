
**An action** refers to a long-running remote procedure call with feedback and the ability to cancel or preempt the goal.
E.g: the high-level state machine running a robot may call action to tell the navigation subsystem to travel to a waypoint, **which may take several seconds (or minutes)** to do. Along the way, the navigation subsystem can provide **feedback** on how far along it is, and the high level has the option to **cancel or preempt** the travel to that way point

Actions are expected to be long running procedures, consider to use **services** instead if it is short running remote procedure call.

An actions consists of two parts : **the action server and the action client** 

## Action Server
- Accepts and executes the action request
- Sends feedback during execution
- Handles cancellation or preemption
E.g: navigation subsystem
**NOTE** there should only ever be one action server per action name.
## Action Client
- Sends a request to the action server
- Receives results and feedback
- Can be a lot of action clients using the same action name

![[Pasted image 20251011234858.png]]

## TASKS
### 1 Setup
`ros2 run turtlesim turtlesim_node`
`ros2 run turtlesim turtle_teleop_key`

### 2 Use actions
In the `teleop_turtle` node, you will see message using selected keys to rotate the turtle. The `F` key will cancel a goal mid-execution.
Both client and the server can cancel a goal mid-execution

### 3 ros2 node info
`ros2 node info turtlesim`
`$ Action server`
`$ /turtle1/rotate_absolute: turtlesim/action/RotateAbsolute`
turtlesim acts as **Action server** that receives rotation goals, performs, and send feedbacks and results

`ros2 node info /teleop_turtle`
`$ Action server`
`$ /turtle1/rotate_absolute: turtlesim/action/RotateAbsolute`
teleop_turtle acts as **Action client** that sends rotation goals, performs and send feedbacks and results

### 4 ros2 action list
List all current action(s)

### 5 ros2 action type "name"
check action type

### 6 ros2 action info
`ros2 action info /turtle1/rotate_absolute
`Action: /turtle1/rotate_absolute
`Action clients: 1
 `   /teleop_turtle
`Action servers: 1
  `  /turtlesim

### 7 ros2 interface show
`ros2 interface show turtlesim/action/RotateAbsolute`
`# The desired heading in radians
`float32 theta `

`# The angular displacement in radians to the starting position
`float32 delta

`# The remaining rotation in radians
`float32 remaining`

### 8 ros2 action send_goal
`ros2 action send_goal <action_name> <action_type> <values>`
`ros2 action send_goal /turtle1/rotate_absolute turtlesim/action/RotateAbsolute "{theta: 1.57}`

All goals have a unique ID, shown in the return message. You can also see the result
To see the feedback add `--feedback`























