#beginner #workspace #colcon 
**Goal** : create a workspace and learn how to set up an overlay for development and testing.
## Background 
A workspace is a dir containing ROS 2 package. Before using ROS 2, it's necessary to source your ROS 2 installation workspace in the terminal you plan to work in. This makes ROS 2's packages available for you to use in that terminal.

You also have the option of sourcing "overlay" - a secondary workspace where you can add new packages without interfering with the existing ROS 2 workspace that you're extending, or "underlay". Your underlay must contain the dependencies of all the packages in you overlay
Packages in your overlay will override packages in the underlay. It's also possible to have several layers of underlays and overlays.

## TASKS
### 1 Source ROS 2 environment
Your main ROS 2 installation will be your underlay for this tutorial (not necessarily to the main ROS 2 installation)

`source /opt/ros/jazzy/setup.bash`

### 2 Create a new directory

Best practice is to create a new directory for every new workspace. 
`mkdir  -p ~/ros2_ws/src`
`cd ~/ros2_ws/src`

Another best practice is to put any packages in your workspace into the `src` directory.

### 3 Clone a sample repo

`git clone https://github.com/ros/ros_tutorials.git -b jazzy`

### 4 Resolve dependencies
Before building the workspace, you need to resolve the package dependencies.

Make it back ros2_ws

`cd ..`
`rosdep install -i --from-path src --rosdistro jazzy -y`

Packages declare their dependencies in the **package.xml**

### 5 Build the workspace with colcon

`colcon build`
Other useful arguments for `colcon build`

`--packages-up-to` builds the package you want, plus all its dependencies, but not the whole workspace
`--symlink-install` saves you from having to rebuild every time you tweak python scripts
`--event-handlers console_direct+` shows console output while building (can otherwise be found in the `log` directory)    
 `--executor sequential` processes the packages one by one instead of using parallelism

### 6 Source the overlay

source the underlay first
`source /opt/ros/jazzy/setup.bash`

source the overlay first
`cd ~/ros2_ws`
`source install/local_setup.bash`

**NOTE** : sourcing the `local_setup` of the overlay will only add the packages available in the overlay to your environment. `setup` sources the overlay and the underlay
So sourcing your main ROS 2 installation `setup` and then the `ros2_ws` overlay's `local_setup` is the same as just sourcing the `ros2_ws`'s `setup`, because that includes the environment and its underlay

`ros2 pkg prefix turtlesim`
check what source

### 7 Modify the overlay



















































