
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