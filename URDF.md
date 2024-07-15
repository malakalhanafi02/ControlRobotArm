# What is URDF?

Unified Robot Description Format
- an XML format used in ROS to describe a robot model
- the URDF specification defines the properties of the robot in terms of its physical configuration (structure, joints, links, sensors, and actuators)


## Key Components of URDF:
<img width="305" alt="image" src="https://github.com/user-attachments/assets/054342c7-75bd-42a8-bc0e-62e08ab36d93">

### 1. Links:

- Represent the rigid bodies of the robot.
- Each link can have visual, collision, and inertial properties.

### 2. Joints:

- Define the relationship between two links.
- Can specify different types of joints, such as fixed, revolute, prismatic, and continuous.

### 3. Visuals:

- Describe how the link should be displayed in simulations and visualization tools.

### 4. Collisions:

- Define the collision properties for physical simulations and interactions.

### 5. Inertials:

- Specify the mass and inertia properties for dynamic simulations.

### 6. Sensors and Actuators:

- Describe the sensors and actuators attached to the robot.


## Example Code:
```bash
<?xml version="1.0"?>
<robot name="robot1">

  <!-- Link 1 -->
  <link name="base_link">
    <visual>
      <geometry>
        <box size="1 1 1"/>
      </geometry>
      <material name="blue"/>
    </visual>
    <collision>
      <geometry>
        <box size="1 1 1"/>
      </geometry>
    </collision>
    <inertial>
      <mass value="1.0"/>
      <inertia ixx="0.1" ixy="0.0" ixz="0.0" iyy="0.1" iyz="0.0" izz="0.1"/>
    </inertial>
  </link>

  <!-- Link 2 -->
  <link name="upper_link">
    <visual>
      <geometry>
        <cylinder length="1" radius="0.1"/>
      </geometry>
      <material name="green"/>
    </visual>
    <collision>
      <geometry>
        <cylinder length="1" radius="0.1"/>
      </geometry>
    </collision>
    <inertial>
      <mass value="0.5"/>
      <inertia ixx="0.05" ixy="0.0" ixz="0.0" iyy="0.05" iyz="0.0" izz="0.05"/>
    </inertial>
  </link>

  <!-- Joint connecting the two links -->
  <joint name="joint1" type="revolute">
    <parent link="base_link"/>
    <child link="upper_link"/>
    <origin xyz="0 0 0.5" rpy="0 0 0"/>
    <axis xyz="0 0 1"/>
    <limit effort="1.0" velocity="1.0" lower="-1.57" upper="1.57"/>
  </joint>

</robot>

```









