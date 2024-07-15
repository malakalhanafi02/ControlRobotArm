# 🦾 Controlling the Robot Arm by joint_state_publisher 🦾

https://github.com/user-attachments/assets/5f0fbf12-9d86-47d3-bae5-8f82b88bdf43

## ⚠️ Prerequisites: Create a Catkin workspace

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

## 🤖 Clone the `arduino_robot_arm` Package

1. Navigate to the src folder of your workspace:

```bash
cd ~/catkin_ws/src
 ```
2. Install Git if you haven't already:
```bash
sudo apt install git
 ```
3. Clone the arduino_robot_arm repository:
```bash
git clone https://github.com/smart-methods/arduino_robot_arm
 ```
4. Install Dependencies:
```bash
cd ~/catkin_ws
rosdep install --from-paths src --ignore-src -r -y
sudo apt-get install ros-noetic-moveit
sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
 ```
5. Compile the catkin workspace:
```bash
catkin_make
 ```
6. Verify Installation:
```bash
rospack list
 ```

Should look something like this when compiled successfully!

<img width="638" alt="image" src="https://github.com/user-attachments/assets/5132ee36-dffe-4ad6-8608-7ea5fc1d66fc">

## 🎮 Control the motors and Visualize them in RViz

#### The following command will launch the RViz visualization tool and use the `joint_state_publisher` to control the joints of the robot:
```bash
roslaunch robot_arm_pkg check_motors.launch
```

<img width="1275" alt="image" src="https://github.com/user-attachments/assets/92e3838f-973b-4381-b7a5-330c7d85ed79">



#### The GUI allows you to control the joint states using sliders to adjust the angles of different joints, and you should see the robot model update in real-time:

<img width="214" alt="image" src="https://github.com/user-attachments/assets/e683bd80-4a4f-4edf-8d15-d05e3dc307b1">


#### To visualize the node graph and understand the communication between nodes, use the following command:
```bash
rqt_graph
```
#### This will open a window showing the nodes and topics in your ROS system:
<img width="594" alt="image" src="https://github.com/user-attachments/assets/1301fab8-ad75-4883-ab52-74689f6e1267">

#### To see the actual values being published to the `/joint_states topic`, use the following command:
```bash
rostopic echo /joint_states
```
<img width="637" alt="image" src="https://github.com/user-attachments/assets/936c5502-f6e1-488a-9085-9a2d256618bd">

## 👾 Launching the Simulation in Gazebo

#### The following command will launch Gazebo with the robot model and use the joint_state_publisher` to control the joints of the robot in the simulation:
```bash
roslaunch robot_arm_pkg check_motors_gazebo.launch
```

<img width="1264" alt="image" src="https://github.com/user-attachments/assets/1139208a-d554-4136-8a4b-eb01810266c5">

## 👩🏻‍💻 Running the Python Script

#### The Python script `joint_states_to_gazebo.py` ensures that the joint states from the `joint_state_publisher` are properly communicated to the Gazebo simulation:
```bash
cd ~/catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts
sudo chmod +x joint_states_to_gazebo.py
rosrun robot_arm_pkg joint_states_to_gazebo.py
```


<img width="1678" alt="image" src="https://github.com/user-attachments/assets/1244f046-bee8-43b1-be73-80ca1aeb7cba">

#### Running `rqt_graph` to show the connections between the nodes

<img width="669" alt="image" src="https://github.com/user-attachments/assets/8211f172-4b7f-4c88-b1e8-83ab8119ae65">


