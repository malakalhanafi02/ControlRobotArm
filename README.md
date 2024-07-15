# Controlling the Robot Arm by joint_state_publisher

## Create a Catkin workspace


1. Source the ROS Noetic setup file:
```bash
source /opt/ros/noetic/setup.bash
```

2. Create and build a Catkin workspace:
```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```

3. Source the workspace:
```bash
source devel/setup.bash
```

4. Add the workspace to your .bashrc to source it automatically:
```bash
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
```

