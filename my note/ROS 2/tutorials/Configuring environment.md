#beginner #environmet

## BACKGROUND
**ROS 2** relies on the notion of combining workspaces during the shell environment.
**"Workspaces"** is a ROS term for the location on your system where you're developing with ROS 2.
The core **ROS 2** workspace is called the **underlay**.
Subsequent local workspaces are called **overlays**.
When developing with **ROS 2**, you will typically have several workspaces active concurrently.

This is accomplisehed by sourcing setup file every time you open a new shell
## TASKS
### 1. Source the setup files
Run this command on every new shell you open to have access to **ROS 2**.

`source /opt/ros/jazzy/setup.bash`

### 2. Add sourcing to your shell startup script
In order to automate the first step -> run this to add the command to your startup shell script
 `echo "source /opt/ros/jazzy/setup.bash`

### 3. Check environment variables
 ` printenv | grep -i ROS`


`ROS_VERSION=2
`ROS_PYTHON_VERSION=3
`ROS_DISTRO=jazzy`
 
#### 3.1 The `ROS_DOMAIN_ID` variable

**purpose** : Domain ID isolates ROS 2 communication group using DDS (Data Distribution Service) . Node on the same domain can communicate, nodes on different domains cannnot.

**default domain** = 0

**choosing a domain ID**
- quick choice : choose **between 0-101 (inclusive)**
- mathematical range:  the **domain ID** is used by DDS to compute **UDP** ports. The **UDP** ports is an unsigned 16-bit integer -> highest number that can be allocated is 65535. The highest domain ID that can possibly be assigned is 232, while the lowest can be assigned is 0.

**platform-specific constraint**
It is best to avoid allocating domain IDs in the operating systems's **ephemeral port range**. This avoids possible conflicts between the ports used by **ROS 2** nodes and other networking services on the computers

**Linux**: ephemeral ports are 327678 - 60999-> safe domain IDs 0-101 and 215-232.

**participant constraints**
For each **ROS 2** process running on a computer, one DDS "participant" is created.
Since each DDS participant takes up two ports on the computer, running more 120 -> conflict

Once you have determined a unique integer for your group of **ROS 2** nodes, you can use.
`export ROS_DOMAIN_ID = <YOUR_DOMAIN_ID>`

To maintain this between shell sessions, you can add the command to your shell startup script
`echo "export ROS_DOMAIN_ID = <YOUR_DOMAIN_ID>" >>~/.bashrc`

#### 3.2 The `ROS_AUTOMATIC_DISCOVERY_RANGE` variable
By default **ROS 2** communication is not limited to localhost. `ROS_AUTOMATIC_DICOVERY_RANGE` environment  variables allow you to limit **ROS 2** discovery range, which is helpful in certain settings like where multiple robots may publish to the same topic causing strange behaviors.