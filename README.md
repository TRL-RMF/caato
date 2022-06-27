# CAATO
## About
Changi Airport Autonomous Trolley Operator (CAATO)
## Installation Instructions
### Prerequisites
* [Ubuntu 18.04 LTS](https://releases.ubuntu.com/18.04/)
* [ROS1 - Melodic](https://wiki.ros.org/melodic)

Install all non-ROS prerequisite packages
```bash
sudo apt update && sudo apt install \
  git wget \
  python-rosdep \
  python-catkin-tools \
  python3-vcstool
```

### Workspace Setup

```bash
mkdir -p ~/ws_caato/src
cd ~/ws_caato/src
git clone https://git.siotgov.tech/decada_robotics/caato.git
git clone https://git.siotgov.tech/decada_robotics/roboteq_diff_driver.git

```
Install all ROS dependencies through `rosdep`

```bash
cd ~/ws_caato
source /opt/ros/melodic/setup.bash
rosdep install --from-paths src --ignore-src -y -r
```
Build
```bash
cd ~/ws_caato
catkin build
```

## Usage
### Tele-operation
It is convenient to operate the AGV over wireless controllers. Here we use the Sony [DS4](http://wiki.ros.org/ds4_driver).

1. Follow the instructions in the official [ds4_driver](https://github.com/naoki-mizuno/ds4_driver) to install `ds4drv` and `udev` rules

2. Install the ds4 driver under ROS
```bash
cd ~/ws_caato/src
git clone https://git.siotgov.tech/decada_robotics/ds4_driver.git
```
3. Launch the ds4 tele-operation:
```roslaunch caato_teleop ds4.launch```

### Mapping
```roslaunch caato_teleop gmapping_bringup.launch```

### Navigation
```bash
roslaunch caato_navigation navigation.launch
```