  # 6DoF Object Grasping by Aubo-i5 Manipulator & D415
  
**Ubuntu version: 20.04**

## Preparation
- Configure the network setting

- Download the code:
```
git clone https://github.com/Zzzzleeii/Aubo_i5/aubo_ws.git
```

- Add to **.bashrc** file:
```
source devel/setup.bash
```

## Moveit! Test

```
roslaunch aubo_i5_moveit_config moveit_planning_execution.launch robot_ip:=192.168.31.10
```

## Installation of Intel Realsense2

- Install Depencencies:
```
sudo apt-get install libssl-dev libusb-1.0-0-dev libudev-dev pkg-config libgtk-3-dev
sudo apt-get install libglfw3-dev libgl1-mesa-dev libglu1-mesa-dev at
```

- [Installation, uninstallation, upgradation of the SDK](https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md#uninstalling-the-packages) 

- Run & Test:
```
realsense-viewer
```

- Installation of ROS Package:
```
sudo apt-get install ros-noetic-realsense2-*
```

[**Care for the version of SDK and Firmwire!!**](https://dev.intelrealsense.com/docs/firmware-releases-d400)

## Easy Handeye Eye-in-Hand Calibration

- Steps for the calibration:
```
roslaunch realsense2_camera rs_rgbd.launch
roslaunch aubo_i5_moveit_config moveit_planning_execution.launch sim:=false robot_ip:=192.168.31.10
roslaunch easy_handeye aubo_realsense_calibration.launch
```

> ### Attention!!

- If there has no rs_rgbd:
```
sudo apt-get install ros-noetic-rgbd-launch
```

- Without Anaconda environment:
```
catkin build -j2 -DCATKIN_WHITELIST_PACKAGES="Your Package Name" -DPYTHON_EXECUTABLE=/usr/bin/python3
```
