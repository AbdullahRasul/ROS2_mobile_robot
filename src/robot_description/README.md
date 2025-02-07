# Robot Description Package

This package contains the URDF (Unified Robot Description Format) and meshes for the mobile robot. The URDF is used to describe the physical structure and joints of the robot. It also includes the necessary meshes for visualization in RViz.

## Project Overview

The **robot_description** package contains:

- **URDF files**: These describe the robot's physical configuration, links, and joints.
- **Meshes**: STL files representing the 3D models of the robot parts (e.g., base_link, wheels).
- **Xacro files**: Parametric XML files used to generate the URDF.

### Key Components
- `urdf/robot.urdf.xacro`: The main URDF file that describes the robot.
- `meshes/`: Contains the 3D models of the robot parts in STL format.

## Running the Robot in ROS 2

Follow these steps to load the robot description and visualize it in RViz.

### 1. Run the Robot State Publisher

The **robot_state_publisher** node is responsible for publishing the robot's joint states and transforming between the links based on the robot's URDF.

Run the following command to launch the **robot_state_publisher** with the URDF file:

```bash
ros2 run robot_state_publisher robot_state_publisher --ros-args -p robot_description:="$(xacro /home/user/ROS2_mobile_robot/src/robot_description/urdf/robot.urdf.xacro)"
```


Run the following command to launch the **joint_state_publisher_gui** with the URDF file:

```bash
ros2 run joint_state_publisher_gui joint_state_publisher_gui
```

Run the following command to launch the **visualization** with the URDF file:

```bash
ros2 run rviz2 rviz2
```

### **What to Do in RViz**

**Set the Origin/Map to base_footprint**:
   - In the **RobotModel** properties, set the **Fixed Frame** to `base_footprint` for correct robot alignment.
   

**Add the Robot Model**:
   - In the **Displays** panel, click **Add** and select **RobotModel**.
   - Set the **Robot Description** to the `robot_description` parameter that holds the URDF model.




