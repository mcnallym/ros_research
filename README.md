# ros_research
## SETUP
### [Multipass](https://canonical.com/blog/ros-development-on-linux-windows-and-macos)
- brew install multipass
- multipass launch ros2-humble --name humble-vm --mount ~/Documents/Work/Reliabotics/ros_research:./ros_research
- multipass shell humble-vm

### Environment Setup
- source /opt/ros/humble/setup.bash (echoed to .bashrc so no need to run everytime)
- export ROS_DOMAIN_ID=1
- export ROS_LOCALHOST_ONLY=1

## Tutorials
https://docs.ros.org/en/humble/Tutorials.html

## ROS Notes
### Nodes
Each node in ROS should be responsible for a single, modular purpose. Each node can send and receive data from other nodes via topics, services, actions, or parameters.

#### RUN
> ros2 run <package_name> <executable_name>
- Launches an executable from a package.

> ros2 run <package_name> <executable_name> --ros-args --params-file <file_name>
- Starts a same node using your saved parameter values

#### LIST
> ros2 node list
- Shows the names of all running nodes.

#### Remapping
> --ros-args --remap __node:<node_name>
- Allows you to reassign default node properties, like node name, topic names, service names, etc., to custom values.

#### INFO
> ros2 node info <node_name>
- Returns a list of subscribers, publishers, services, and actions. i.e. the ROS graph connections that interact with that node.

### Topics
Topics act as a bus for nodes to exchange messages. A node may publish data to any number of topics and simultaneously have subscriptions to any number of topics.

#### LIST
> ros2 topic list
- Returns a list of all the topics currently active in the system.

> ros2 topic list -t
- Returns the same list of topics, this time with the topic type appended in brackets.

#### ECHO
> ros2 topic echo <topic_name>
- Shows the data being published on a topic

#### INFO
> ros2 topic info <topic_name>
- Returns the type of the topic, the publisher count, and the subscriber count

#### INTERFACE SHOW
> ros2 interface show <msg type>
- Returns what structure of data the message expects.

#### PUB
> ros2 topic pub <topic_name> <msg_type> <args> <
- Publish data onto a topic directly from the command line.
The '<args>' argument is the actual data you’ll pass to the topic, in the structure you just discovered in the previous section.
It’s important to note that this argument needs to be input in YAML syntax.

> --once
> - an optional argument meaning “publish one message then exit”.
>
> --rate <frequency> <


#### HZ
> ros2 topic hz <topic_name>
- View the rate at which data is published using.

### Services
Services are based on a call-and-response model versus the publisher-subscriber model of topics. Services only provide data when they are specifically called by a client.

#### LIST
> ros2 service list
- Returns a list of all the services currently active in the system

> ros2 service list -t
- Returns the same list of services, this time with the topic type appended in brackets.

#### TYPE
Services have types that describe how the request and response data of a service is structured. Service types are defined similarly to topic types, except service types have two parts: one message for the request and another for the response.

> ros2 service type <service_name>
- Returns the type of service.

#### FIND
> ros2 service find <type_name>
- Finds all the services of a specific type.

#### INTERFACE SHOW
> ros2 interface show <type_name>
- Returns the structure of the input arguments of the service type.

#### CALL
> ros2 service call <service_name> <service_type> <arguments>
- Calls a service. The <arguments> part is optional.

### Parameters
A parameter is a configuration value of a node. Can be integers, floats, booleans, strings, and lists. Each node maintains its own parameters.

#### LIST
> ros2 param list
- Returns the parameters belonging to your nodes.

#### GET
> ros2 param get <node_name> <parameter_name>
- Returns the type and current value of a parameter.

#### SET
> ros2 param set <node_name> <parameter_name> <value>
- Changes a parameter’s value at runtime

#### DUMP
> ros2 param dump <node_name>
- Returns all of a node’s current parameter values.

> ros2 param dump <node_name> > <file_name>
- Saves all of a node's current parameter values to a file.

#### LOAD
> ros2 param load <node_name> <parameter_file>
- Loads parameters from a file to a currently running node.

### Actions
Actions are communication types intended for long running tasks. They consist of three parts: a goal, feedback, and a result. Actions are built on topics and services. Their functionality is similar to services, except actions can be canceled. They also provide steady feedback, as opposed to services which return a single response. Actions use a client-server model, similar to the publisher-subscriber model. An “action client” node sends a goal to an “action server” node that acknowledges the goal and returns a stream of feedback and a result.

#### LIST
> ros2 action list
- Identifies and returns all the actions in the ROS graph.

> ros2 action list -t
- Identifies and returns all the actions, including their types, in the ROS graph.

#### INFO
> ros2 action info <action_name>
- Returns the action, the clients, and the servers.

#### INTERFACE SHOW
> ros2 interface show <action_type>
- Returns the structure of the input arguments of the action.

#### SEND_GOAL
> ros2 action send_goal <action_name> <action_type> <values>
- Sends an action goal from the command line. <values> need to be in YAML format.

## SETUP ISSUES
1. [GUI Not Showing](https://multipass.run/docs/set-up-a-graphical-interface#heading--rdp-on-macos)

2. [Can't access root/.bashrc](https://www.cyberciti.biz/faq/become-superuser-on-ubuntu-linux/)
