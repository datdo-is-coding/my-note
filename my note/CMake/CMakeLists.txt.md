**CMakeLists.txt** is the configuration file
You need to tell it where your sources are and your `build` files

```
cmake [options] <path-to-source>
cmake [options] <path-to-existing-build>
cmake [options] -S <path-to-source> -B <path-to-build>

```

e.g `$ cmake -S  ../../ -B .`
-S 2 folders back
-B the dot means the current folder

**e.g**
```
cmake_required_minimum(VERSION 3.12.3)

project(hello)

add_executable(${PROJECT_NAME} main.cpp)

```

`project(<project_name>)`
`add_executable(<name_of_exe> <source_file>)`
`$PROJECT_NAME`: project name variable
