
## FAST-LIO
**FAST-LIO** (Fast LiDAR-Inertial Odometry) is a computationally efficient and robust LiDAR-inertial odometry package. It fuses LiDAR feature points with IMU data using a tightly-coupled iterated extended Kalman filter to allow robust navigation in fast-motion, noisy or cluttered environments where degeneration occurs. Our package address many key issues:
1. Fast iterated Kalman filter for odometry optimization;
2. Automaticaly initialized at most steady environments;
3. Parallel KD-Tree Search to decrease the computation;


**Related papers**: 

[FAST-LIO2: Fast Direct LiDAR-inertial Odometry](doc/Fast_LIO_2.pdf)

[FAST-LIO: A Fast, Robust LiDAR-inertial Odometry Package by Tightly-Coupled Iterated Kalman Filter](https://arxiv.org/abs/2010.08196)


## Quickly Run with Zvision_1/3/5/5_MT

**For ROS1 Users**: Please switch to the **ros1** branch and follow the instructions at [ros1 branch](https://github.com/Liansheng-Wang/Super-LIO/tree/ros1)

## 1. Prerequisites
### 1.1 **Ubuntu** and **ROS**
**Ubuntu >= 22.04**

The **default from apt** PCL and Eigen is enough for FAST-LIO to work normally.

ROS >= Foxy (Recommend to use ROS-Humble). [ROS Installation](https://docs.ros.org/en/humble/Installation.html)


### 1.2. **PCL && Eigen**
PCL    >= 1.8,   Follow [PCL Installation](https://pointclouds.org/downloads/#linux).

Eigen  >= 3.3.4, Follow [Eigen Installation](http://eigen.tuxfamily.org/index.php?title=Main_Page).


## 2. Build
Clone the repository and colcon build:

```bash
    cd <ros2_ws>/src # cd into a ros2 workspace folder
    git clone https://github.com/ZVISION-lidar/FAST_LIO_ZVISION.git --recursive
    cd ..
    rosdep install --from-paths src --ignore-src -y
    colcon build --symlink-install
```


## 3. Directly run with zvision

### 3.1 Run use ros launch

Launch zvision ros driver.

```bash
cd <yourself_zvision_ros_driver_ws>
source install/setup.bash # use setup.zsh if use zsh
ros2 launch zvlidar_sdk run.py
```


Launch fastlio2.
```bash
cd <ros2_ws>
source install/setup.bash # use setup.zsh if use zsh
ros2 launch fast_lio mapping_zvision_nz1.launch.py # depend on yourself lidar model: ros2 launch fast_lio mapping_zvision_nz*(1/3/5/5_MT).launch.py 
```


### 3.2 PCD file save

Enable `pcd_save.pcd_save_en` in the config file and set the `map_file_path` to the path where the map will be saved.

```pcl_viewer scans.pcd``` can visualize the point clouds.

