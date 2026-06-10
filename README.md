# 🤖 ROS 2 SLAM Simulation

A complete ROS 2 Humble simulation project featuring a full URDF robot model with LiDAR and camera sensors, and pre-configured Gazebo Classic launch files for running SLAM out of the box.

---

## ✨ Features

- Complete URDF robot model with joints, links, and sensor plugins
- LiDAR and camera sensors configured for Gazebo Classic
- Ready-to-use Gazebo Classic launch files — no extra configuration needed
- SLAM integration using `slam_toolbox` for real-time mapping and localization
- Compatible with ROS 2 Humble out of the box

---

## 🛠️ Prerequisites

- Ubuntu 22.04
- [ROS 2 Humble](https://docs.ros.org/en/humble/Installation.html)
- Gazebo Classic (11)
- `slam_toolbox`

```bash
# Install Gazebo Classic and ROS 2 bridge
sudo apt install gazebo ros-humble-gazebo-ros-pkgs

# Install SLAM Toolbox
sudo apt install ros-humble-slam-toolbox

# Install RViz2 and other tools
sudo apt install ros-humble-rviz2 ros-humble-robot-state-publisher ros-humble-joint-state-publisher
```

---

## 🚀 Getting Started

**1. Clone the repository**
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

**2. Install dependencies**
```bash
rosdep install --from-paths src --ignore-src -r -y
```

**3. Build the workspace**
```bash
colcon build
source install/setup.bash
```

**4. Launch Gazebo Classic simulation**
```bash
ros2 launch your_package gazebo.launch.py
```

**5. Launch SLAM**
```bash
ros2 launch your_package slam.launch.py
```

**6. Visualize in RViz2**
```bash
ros2 launch your_package rviz.launch.py
```

---

## 🗺️ Saving the Map

Once you're happy with the map built by SLAM Toolbox:

```bash
# Save map via ROS 2 service call
ros2 run nav2_map_server map_saver_cli -f ~/my_map

# Or save via slam_toolbox service
ros2 service call /slam_toolbox/save_map slam_toolbox/srv/SaveMap "name: {data: 'my_map'}"
```

---

## 🔍 Useful Commands

```bash
# Check active topics
ros2 topic list

# View LiDAR scan data
ros2 topic echo /scan

# View camera feed topic
ros2 topic echo /camera/image_raw

# Check TF tree
ros2 run tf2_tools view_frames

# Monitor robot state
ros2 topic echo /robot_description
```

---

## 📁 Project Structure

```
├── description/        # Robot URDF/Xacro model files
├── launch/             # ROS 2 Gazebo Classic launch files
├── config/             # SLAM Toolbox and RViz2 config files
├── worlds/             # Gazebo Classic world files
├── CMakeLists.txt            
└── package.xml             
```
