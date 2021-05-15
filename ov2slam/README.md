# OV²SLAM

Adapt from the official OV²SLAM [repo](https://github.com/ov2slam/ov2slam.git).

## 1. Installation

### 2.0 Clone

Clone the git repository in your catkin workspace:

### 2.1 Build Thirdparty libs

For convenience we provide a script to build the Thirdparty libs:

```
    cd ~/catkin_ws/src/ov2slam
    chmod +x build_thirdparty.sh
    ./build_thirdparty.sh
```

**WATCH OUT** By default, the script builds obindex2, ibow-lcd, sophus and ceres.  If you want to use your own version of Sophus or Ceres 
you can comment the related lines in the script.  Yet, about Ceres, as OV²SLAM is by default compiled with the "-march=native" flag, the 
Ceres lib linked to OV²SLAM must be compiled with this flag as well, which is not the default case (at least since Ceres 2.0).  The _*build_thirdparty.sh*_ script ensures that Ceres builds with the "-march=native" flag.

If you are not interested in the Loop Closing feature of OV²SLAM, you can also comment the lines related to obindex2 and ibow-lcd.

**(Optional)** Install OpenGV:

```
    cd your_path/
    git clone https://github.com/laurentkneip/opengv
    cd opengv
    mkdir build
    cd build/
    cmake ..
    sudo make -j4 install
```


### 2.2 Build OV²SLAM

Build OV²SLAM package with your favorite catkin tool:

```
    cd ~/catkin_ws/src/ov2slam
    catkin build --this
    source ~/catkin_ws/devel/setup.bash
```

OR

```
    cd ~/catkin_ws/
    catkin_make --pkg ov2slam
    source ~/catkin_ws/devel/setup.bash
```

## 3. Usage

Update the original repo: Read an image sequence from a folder instead of subscribing to a rosbag.
Run OV²SLAM using:

```
    rosrun ov2slam ov2slam_node parameter_file.yaml
```