# Introduction
This article primarily introduces how to install SLAMTEC LIDAR ROS2 on the Ubuntu 22.04 environment provided by Avalue Technology Inc.

# Caution
Please note that the **SLAMTEC LIDAR ROS2 Package** is licensed under the **BSD-2-Clause License**.
Please use it in accordance with its agreement!
Our repository is licensed under the **MIT License**, which applies only to this file: **README.md**.

## Supported SLAMTEC LIDAR

| Lidar Model |
| ---------------------- |
|RPLIDAR A1              |
|RPLIDAR A2              |
|RPLIDAR A3              |
|RPLIDAR C1              |
|RPLIDAR S1              |
|RPLIDAR S2              |
|RPLIDAR S3              |
|RPLIDAR S2E             |
|RPLIDAR T1              |

## Step 1: Install ROS2 Humble, on Ubuntu 22.04
If your target machine does not yet have ROS2 Humble installed, please refer to the following documentation for installation instructions.
Reference - [ros2.humble.ACP-3588](https://github.com/Avalue-Technology/ros2.humble.ACP-3588 "ros2.humble.ACP-3588")
Reference - [ros2.humble.EMS-TGL](https://github.com/Avalue-Technology/ros2.humble.EMS-TGL "ros2.humble.EMS-TGL")

## Step 2: Build SLAMTEC LIDAR ROS2
```bash
# Setup ROS2 Humble Environment
source /opt/ros/humble/setup.bash

cd ~/ros2_ws/src
git clone https://github.com/Slamtec/sllidar_ros2.git
cd ~/ros2_ws/
colcon build --symlink-install --packages-select sllidar_ros2
```

## Setp 3: Configure ROS2 Humble, SLAMTEC LIDAR ROS2 Environment
```bash
# Setup ROS2 Humble Environment
source /opt/ros/humble/setup.bash
# Setup SLAMTEC LIDAR ROS2 Environment
cd ~/ros2_ws
source install/setup.bash
```

# Setp 4: Configure Serial Port
Please modify the Python launch file Serial Port based on the LiDAR Model.
For example, if you choose RPLIDAR A2M12, you should modify: sllidar_a2m12_launch.py, view_sllidar_a2m12_launch.py.
The original Serial Port: /dev/ttyUSB0, you should modify it to /dev/avalue_rplidar.
Because of we have created symbolic link on the LiDAR Serial Port via udev rules.

# Usage
```bash
# RPLIDAR A1
ros2 launch sllidar_ros2 view_sllidar_a1_launch.py

# RPLIDAR A2M7
ros2 launch sllidar_ros2 view_sllidar_a2m7_launch.py

# RPLIDAR A2M8
ros2 launch sllidar_ros2 view_sllidar_a2m8_launch.py

# RPLIDAR A2M12
ros2 launch sllidar_ros2 view_sllidar_a2m12_launch.py

# RPLIDAR A3
ros2 launch sllidar_ros2 view_sllidar_a3_launch.py

# RPLIDAR C1
ros2 launch sllidar_ros2 view_sllidar_c1_launch.py

# RPLIDAR S1
ros2 launch sllidar_ros2 view_sllidar_s1_launch.py

# RPLIDAR S2
ros2 launch sllidar_ros2 view_sllidar_s2_launch.py
ros2 launch sllidar_ros2 view_sllidar_s2e_launch.py

# RPLIDAR S3
ros2 launch sllidar_ros2 view_sllidar_s3_launch.py

# RPLIDAR T1
ros2 launch sllidar_ros2 view_sllidar_t1_launch.py

# RPLIDAR S1 (TCP connection)
ros2 launch sllidar_ros2 view_sllidar_s1_tcp_launch.py
```

# Reference.
[SLAMTEC LIDAR ROS2 Package](https://github.com/Slamtec/sllidar_ros2)