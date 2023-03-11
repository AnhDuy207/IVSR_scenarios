# IVSR_scenarios

## 1. Installation
***
### 2.0. Environments
- **ROS**: tested on [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu) (Ubuntu 18.04)
- **PX4 Firmware**: tested on v10.0.1 - setup [here](https://github.com/congtranv/px4_install)
- **Catkin workspace**: `catkin_ws`
  ```
  ## create a workspace if you've not had one
  mkdir -p [path/to/ws]/catkin_ws/src
  cd [path/to/ws]/catkin_ws
  ```
  ```
  catkin init
  catkin config --extend /opt/ros/melodic
  catkin config --cmake-args -DCMAKE_BUILD_TYPE=Release
  catkin config --merge-devel
  catkin build
  ```
- **MAVROS**: binary installation - setup [here](https://docs.px4.io/master/en/ros/mavros_installation.html#binary-installation-debian-ubuntu)

### 2.1. [AnhDuy207/IVSR_Scenarios](https://github.com/AnhDuy207/IVSR_scenarios) 
```
cd [path/to/ws]/catkin_ws/src
```
```
git clone https://github.com/AnhDuy207/IVSR_scenarios
```

## 2. Usage
***
### 2.1. Simulation
- Terminal 1: Launch px4 sitl simulation
```
roslaunch px4 mavros_posix_sitl.launch
```
- Terminal 2: Launch fly mode
```
source scenarios_ws/devel/setup.bash
```
```
roslaunch offboard plannerMarker.launch simulation:=true
```
Where:

`simulation:=true`: Run simulation then Drone automated Arm 

Terminal show then we choose mode:
[ INFO] Please choose mode
- Choose (1): Takeoff and Hovering
- Choose (2): Takeoff and Landing at marker
- Choose (3): Mission with ENU setpoint and no Obstacle
- Choose (4): Mission with ENU setpoint and Obstacle
- Choose (5): Mission with ENU setpoint, Obstacle and Delivery
- Choose (6): Mission with Planner and Landing at marker

If you run mode (2) or (6), you have to run more commands on other terminal to detect ArUco marker:
```
source scenarios_ws/devel/setup.bash
```
```
rosrun offboard MarkerDetection.py
```
