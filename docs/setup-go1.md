# Setting up the Unitree Go1 Robot
## Table of Contents
- [Turning on the Robot](#turning-on-the-robot)
- [Connecting to the Robot](#connecting-to-the-robot)
    - [Connecting over Ethernet](#connecting-over-ethernet)
    - [Connecting over WiFi](#connecting-over-wifi)

## Turning on the Robot
The process to turn on the GO1 Robot can be found in this [video](https://www.youtube.com/watch?v=VbabuAhol0E).

## Connecting to the Robot
### Connecting over Ethernet
The robot can be connected to via ethernet by turning it on and completing the following steps:
1. Connect the robot and laptop together via an ethernet link.
2. Get the ethernet port name on your computer.
    ``` bash
    sudo ifconfig
    ...
    enp0s25: ... # en* means ethernet port - this is the port we want
    ...
    ```
3. Set a static connection to the robot.
    ``` bash
    sudo ifconfig enp0s25 down # replace with your port name
    sudo ifconfig enp0s25 192.168.123.162/24
    sudo ifconfig enp0s25 up
    ```
4. SSH to test connection.
    ``` bash
    ssh pi@192.168.12.1
    ...
    Password: 123
    ```

### Connecting over WiFi
> [!NOTE]
> The robot produces a 5GHz wifi signal.

The robot can be connected to via wifi by turning it on and completing the following steps:
1. The robot's wifi connection name will start with `Unitree_Go`.
2. The robot's password will be `00000000` (8x zeros).
3. SSH to test connection.
    ``` bash
    ssh pi@192.168.12.1
    ...
    Password: 123
    ```