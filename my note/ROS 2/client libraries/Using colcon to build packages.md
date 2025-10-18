#beginner #colcon
**Goal** : build a ROS2 workspace with `colcon`

## BACKGROUND
`colcon` is an iteration on the ROS build tools `catkin_make`, `catkin_make_isolated`,`catkin_tools`, and `ament_tools`

## INSTALL `colcon`
`sudo apt install python3-colcon-common-extensions`

## BASICS
A ROS workspace is a directory with a particular structure. Commonly there is `src` subdirectory.
Inside that subdirectory is where the source code of ROS packages will be located. Typically the dir starts otherwise empty

colcon performs out of source builds. By default it will create the following directories as peers of the `src` directory
- The `build` dir wll be where intermediate files are stored. For each package a subfolder will be created in which e.g CMake is being invoked
- The `install` directory is where each package will be installed to. By default each will be installed into a separate subdirectory.
- The `log` dir contains variour logging information about each colcon invocation
## CREATE A WORKSPACE
First, create a directory `ros2_ws` to contain our workspace

`$ mkdir -p ~/ros2_ws/src`
`$ cd ~/ros2_ws`

**ADD SOME SOURCES**
`git clone https://github.com/ros2/examples src/examples -b jazzy`

**SOURCE AN UNDERLAY**
It is important that we have sourced the environment for an existing ROS 2 installation that will provide our workspace with **the necessary build dependencies**. We call this env. **an underlay**

Our workspace, `ros2_ws` will be **an overlay** on top of the existing ROS2 installation
It is recommended to use an overlay when you plan to iterate on a small number of packages, rather than putting all of your packages into the same workspaces.

## BUILD THE WORKSPACE
In the root of the workspace, run `colcon build`. Since build types such as `ament_cmake` do not support the concept of the `devel` space and require the package to be installed, colcon supports the option `--symlink-install`. This allows the installed files to be changed by changing the files in the `source` space (e.g. Python files or other non-compiled resources) for faster iteration.

`colcon build --symlink-install`

**SOURCE THE ENV**
When colcon has completed building successfully, the output will be in the `install` directory. Before you can use any of the installed executables or libraries, you will need to add them to your path and library paths. colcon will have generated bash/bat files in the `install` directory to help set up the environment. These files will add all of the required elements to your path and library paths as well as provide any bash or shell commands exported by packages.

**With the environment sourced, we can run executable built by colcon**
`ros2 run examples_rclcpp_minimal_subscriber subscriber_member_function`
`ros2 run examples_rclcpp_minimal_publisher publisher_member_function`

## CREATE YOUR OWN PACKAGE
colcon uses the `package.xml` specification defined in [REP 149](https://www.ros.org/reps/rep-0149.html) ([format 2](https://www.ros.org/reps/rep-0140.html) is also supported).

colcon supports multiple build types. The recommended build types are `ament_cmake` and `ament_python`. Also supported are pure `cmake` packages.

An example of an `ament_python` build is the [ament_index_python package](https://github.com/ament/ament_index/tree/jazzy/ament_index_python) , where the setup.py is the primary entry point for building.

A package such as [demo_nodes_cpp](https://github.com/ros2/demos/tree/jazzy/demo_nodes_cpp) uses the `ament_cmake` build type, and uses CMake as the build tool.

For convenience, you can use the tool `ros2 pkg create` to create a new package based on a template. A full description of creating a package and how to use `ros2 pkg create` is in the upcoming tutorial [create a package](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Creating-Your-First-ROS2-Package.html).

## SETUP `colcon_cd`
The command `colcon_cd` allows you to quickly change the current working directory of your shell to the directory of a package. As an example `colcon_cd some_ros_package` would quickly bring you to the directory `~/ros2_ws/src/some_ros_package`. To set up `colcon_cd` you need to run the following commands to modify your shell startup script:
`echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc`
`echo "export _colcon_cd_root=/opt/ros/jazzy/" >> ~/.bashrc`

## Setup `colcon` tab completion] 

The `colcon` command supports command completion for bash and bash-like shells. The `colcon-argcomplete` package must be installed, and [some setup may be required](https://colcon.readthedocs.io/en/released/user/installation.html#enable-completion) to make it work.

## [Tips](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html#id16)[](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html#tips "Link to this heading")

- If you do not want to build a specific package, then place an empty file named `COLCON_IGNORE` in the directory and it will not be indexed.
    
- If you want to avoid configuring and building tests in CMake packages you can pass: `--cmake-args -DBUILD_TESTING=0`.
    
- If you want to run a single particular test from a package:

`colcon test --packages-select YOUR_PKG_NAME --ctest-args -R YOUR_TEST_IN_PKG`

## Setup colcon mixins

Various command line options are tedious to write and/or difficult to remember.

For example, to change the CMake build type to debug, you normally use:

`colcon build --cmake-args -DCMAKE_BUILD_TYPE=Debug`

To make common command line options easier to invoke this repository makes these “shortcuts” available.

To install the default colcon mixins, run the following:

`colcon mixin add default https://raw.githubusercontent.com/colcon/colcon-mixin-repository/master/index.yaml`

`colcon mixin update default`

Then, try out using the debug mixin:

`colcon build --mixin debug`



























