#beginner #service

## BACKGROUND
Services are another method of communication; a call-and-response model; services only provide data when they are specifically called by a client

## Tasks
### 1 Setup
Startup two turtlesim nodes `\turtlesim` and `\teleop_key

### 2.ros2 service list
return a list of active services in the system

### 3. ros2 service type
Services have types that describe how the request and response data of a service is structured. It is similar to topic types, but it has two messages for request and response

`ros2 service type <service_name>`

`dat@dat-HP-Laptop-15-dy2xxx:~$ ros2 service type /clear
`std_srvs/srv/Empty`

The **empty** type means the services call sends no data when making a request and receives no data when receiving a response

### 4. ros2 service list -t
list all services and their types

### 5. ros2 service find
if you want to find all the services of a specific type
`ros2 service find <type_name>`

### 6. ros2 interface show
You can call services from the command line, but first you need to know the structure of the input argument

`ros2 interface show <type_name>`

### 7. ros2 service call
`ros2 service call <service_name> <service_type> <arguments>`
argument is optional if service_type is **Empty**

lets call `/clear` which its type is empty

### 8. ros2 service echo
To see the data communication between a service client and a service server you can echo the service using

`ros2 service echo <service_name | service_type> <arguments>`

`ros2 service echo` depends on service introspection of a service client and server, that is disabled by default



