# ros_research
## ROUND 2 - [Multipass](https://canonical.com/blog/ros-development-on-linux-windows-and-macos)
- brew install multipass
- multipass launch ros2-humble --name humble-vm --mount ~/Documents/Work/Reliabotics/ros_research:./ros_research
- multipass shell humble-vm

### Inside the vm
- cd ros_research

#### Environment Setup
- source /opt/ros/humble/setup.bash
- export ROS_DOMAIN_ID=1
- export ROS_LOCALHOST_ONLY=1

## Tutorials
https://docs.ros.org/en/humble/Tutorials.html

## General Notes
- Using 'Zed' text editor
- github user = mcnallym
- github email = mmcnally629@gmail.com

## ROS Notes
- Must always run the source and export commands to properly configure ROS2 environment

## SETUP ISSUES
1. GUI Not Showing

[Solution](https://multipass.run/docs/set-up-a-graphical-interface#heading--rdp-on-macos)
