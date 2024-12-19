# Unitree-Go1-Motion-ROS2
Send /cmd_vel commands to the Unitree Go1 robot using ROS2

## Table of Contents
- [Contributors](#contributors)
- [Supports](#supports)
- [Hardware](#hardware)
- [Setup](#setup)
- [Usage](#usage)

## Contributors
Created by [Shaun Altmann](https://github.com/ShaunAlt).

## Supports
To see which ROS versions are supported, see the [snt-arg](https://github.com/snt-arg/unitree_ros) repository.

## Hardware
This project implements the following hardware:
- 1x [Unitree Go1 Robot](https://www.unitree.com/go1).

## Setup
Setup the robot and connect to if using the [Go1 Robot Setup Guide](docs/setup-go1.md).

## Usage
1. Create a new ROS2 workspace.
    ``` bash
    $ source /opt/ros/<ros-distro>/setup.sh
    $ mkdir -p ~/ros2_go1_motion_ws/src
    $ cd ~/ros2_go1_motion_ws/src
2. Clone this GitHub repository.
    ``` bash
    $ git clone --recurse-submodules https://github.com/ShaunAlt-Unitree-Go1/Unitree-Go1-Motion-ROS2.git
    ```
3. Install ROS2 dependencies.
    ``` bash
    $ cd ~/ros2_go1_motion_ws
    $ rosdep install --from-paths src --ignore-src --rosdistro <ros-distro> -y
    ```
4. Build the workspace.
    ``` bash
    $ colcon build --symlink-install
    $ source install/setup.sh
    ```
5. Launch the ROS2 Driver.
    - If connected to the robot over Ethernet:
        ``` bash
        $ ros2 launch unitree_ros unitree_driver_launch.py
    - If connected to the robot over WiFi:
        ``` bash
        $ ros2 launch unitree_ros unitree_driver_launch.py wifi:=true
        ```
    - The robot can now be controlled via the `cmd_vel` ROS2 topic.
        - You can use the teleop keyboard in a new terminal:
            ``` bash
            $ source /opt/ros/<ros-distro>/setup.sh
            $ ros2 run teleop_twist_keyboard teleop_twist_keyboard
            ```