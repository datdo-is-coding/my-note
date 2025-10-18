#beginner #package
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










