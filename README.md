# FAST-LIO-ROS2

## Install

Install ROS2 humble or sing docker images for ros2 humble: 
```
docker pull ros:humble-ros-base
```

## Setup

### Install libs
```
sudo apt update
sudo apt install software-properties-common
sudo apt install -y libboost-all-dev libeigen3-dev libpcl-dev liblapack-dev libsuitesparse-dev libcxsparse3 libgflags-dev libgoogle-glog-dev libgtest-dev unzip 
sudo apt install -y ros-humble-pcl-ros ros-humble-pcl-conversions ros-humble-visualization-msgs  

# Livox SDK2
git clone https://github.com/Livox-SDK/Livox-SDK2.git
cd ./Livox-SDK2/
mkdir build && cd build
cmake .. && make -j
sudo make install

# Ceres 2.1.0
wget -O ceres-solver.zip https://github.com/ceres-solver/ceres-solver/archive/refs/tags/2.1.0.zip
unzip -q ceres-solver.zip -d .
cd ceres-solver-2.1.0
mkdir build
cd build
cmake -DBUILD_SHARED_LIBS=TRUE ..
make -j8
sudo make install

# GTSAM
sudo add-apt-repository ppa:borglab/gtsam-release-4.1
sudo apt install -y libgtsam-dev libgtsam-unstable-dev

```

### Create workspace
```
mkdir -p lidar_ws/src
cd lidar_ws/src

git clone https://github.com/Livox-SDK/livox_ros_driver2.git
git clone https://github.com/tranhien1612/FAST-LIO-ROS2.git

cd src/livox_ros_driver2
./build humble
```

### Run
```
ros2 launch livox_ros_driver2 msg_MID360.launch.py

ros2 launch fast_lio mapping.launch.py
```


# Ref
[FAST_LIO_ROS2](https://github.com/Ericsii/FAST_LIO_ROS2.git)
