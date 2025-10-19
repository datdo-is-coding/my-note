at#beginner #package
## BACKGROUND
### 1 What is a ROS 2 package
A package is an organizational unit for your ROS 2 code. (help others to build and use it easily)

Package creation in ROS 2 uses **ament** as its build system and **colcon** as its build tools. You can create a package using either CMake or Python.

### 2 What makes up a ROS 2 package?
**ROS 2 CMake** minimum required content:
- `CMakeLists.txt` file that describes how to build the code within the package
    
- `include/<package_name>` directory containing the public headers for the package
    
- `package.xml` file containing meta information about the package
    
- `src` directory containing the source code for the package
**ROS 2 Python** minimum required content
- `package.xml` file containing meta information about the package
    
- `resource/<package_name>` marker file for the package
    
- `setup.cfg` is required when a package has executables, so `ros2 run` can find them
    
- `setup.py` containing instructions for how to install the package
    
- `<package_name>` - a directory with the same name as your package, used by ROS 2 tools to find your package, contains `__init__.py`

### 3 Packages in a workspace
A single workspace can consist as many packages as you want, each in their own folder (can be diff build types, but not nested packages)

Best practice is to have `src` folder within your workspace, and to create your package in there.

`workspace_folder/`
    `src/`
      `cpp_package_1/`
          `CMakeLists.txt`
          `include/cpp_package_1/`
          `package.xml`
          `src/`

      `py_package_1/`
          `package.xml`
          `resource/py_package_1`
          `setup.cfg`
          `setup.py`
          `py_package_1/`
      ...
      cpp_package_n/
          `CMakeLists.txt
          `include/cpp_package_n/
          `package.xml
          `src/

## TASKS
### 1 Create a package
Make sure you are in the `src` folder before running the package creation command.
`cd ~/ros2_ws/src`
`ros2 pkg create --build-type ament_cmake --license Apache-2.0 <package_name>`

`ros2 pkg create --build-type ament_python --license Apache-2.0 <package_name>`

### 2 Build a package
You can build packages or build each package individually
`cd ~/ros2_ws`

`colcon build`

`colcon build --package-select my_package`

### 3 Source the setup file

To use your new package and executable, open terminal and source your workspace

`source install/local_setup.bash`

### 4 Use the package
`ros2 run my_package my_node`

### 5 Examine package contents

src/hello
├── CMakeLists.txt
├── include
│   └── hello
├── LICENSE
├── package.xml
└── src
    └── main.c

src/py
├── LICENSE
├── package.xml
├── py
│   ├── hello_world.py
│   └── __init__.py
├── resource
│   └── py
├── setup.cfg
├── setup.py
└── test
    ├── test_copyright.py
    ├── test_flake8.py
    └── test_pep257.py

### 6 Customize package.xml
The fields **description** and **license**  contain **TODO** notes. They are not automatically set. The **maintainer** field may also need to be filled in

C++ package

```
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>hello</name>
  <version>0.0.0</version>
  <description>TODO: Package description</description>
  <maintainer email="dat30581@gmail.com">dat</maintainer>
  <license>Apache-2.0</license>

  <buildtool_depend>ament_cmake</buildtool_depend>

  <test_depend>ament_lint_auto</test_depend>
  <test_depend>ament_lint_common</test_depend>

  <export>
    <build_type>ament_cmake</build_type>
  </export>
</package>
```


```
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>py</name>
  <version>0.0.0</version>
  <description>TODO: Package description</description>
  <maintainer email="dat30581@gmail.com">dat</maintainer>
  <license>Apache-2.0</license>

  <test_depend>ament_copyright</test_depend>
  <test_depend>ament_flake8</test_depend>
  <test_depend>ament_pep257</test_depend>
  <test_depend>python3-pytest</test_depend>

  <export>
    <build_type>ament_python</build_type>
  </export>
</package>

```

You can update maintainer, description and everything ends with **_ depend**. This is where your package.xml would list its dependencies on other packages, for colcon to search for.  


**NOTE** for the Python package there is a file called **setup.py**
It contains the same description, maintainer and license fields as package.xml, so you need to set those as well and they should be perfectly match.

Edit **maintainer, maintainer_email, and description** lines to match **package.xml**.























