# 🤖 TurtleBot3 Autonomous Navigation using ROS Noetic
**SLAM + AMCL + Move Base | Gazebo + RViz | Final Project (LEAP)**

[![ROS](https://img.shields.io/badge/ROS-Noetic-blue.svg)](https://wiki.ros.org/noetic)
[![Gazebo](https://img.shields.io/badge/Simulator-Gazebo-lightgrey.svg)](https://gazebosim.org/)
[![Language](https://img.shields.io/badge/Language-Python%20%2B%20Launch-orange.svg)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/Platform-WSL%20Ubuntu%2020.04-lightblue.svg)](https://ubuntu.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> 🧭 *Autonomous TurtleBot3 navigation using ROS Noetic, GMapping, and AMCL — simulated in Gazebo with real-time RViz visualization.*

---

## 🧭 LEAP Final Project – TurtleBot3 Autonomous Navigation

### 👩‍💻 Author

**Name:** Meghna Pradeep
**GitHub:** [@Megge5](https://github.com/Megge5)
**Institute:** Muthoot Institute of Technology and Science (MITS)
**Program:** B.Tech in Electronics and Communication Engineering

---

### 🚀 Project Overview

This project demonstrates **autonomous navigation** of a TurtleBot3 Burger robot in a Gazebo environment using ROS Noetic.

It includes:

* SLAM-based mapping of an indoor environment
* Localization using AMCL
* Autonomous navigation to multiple goals using the move_base package
* Visualization through RViz with costmaps and navigation paths

The project was developed and tested in **Gazebo (with GUI)** on **Windows 11 (WSL Ubuntu 20.04)**.

---

### 🧩 Deliverables Included

| Type                | File / Folder                                                                   | Description                                          |
| ------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------- |
| 🌍 World File       | `worlds/turtlebot3_world.world`                                                 | Default Gazebo world used for mapping and navigation |
| 🧭 Launch Files     | `launch/final_project.launch`, `launch/slam.launch`, `launch/navigation.launch` | For launching different project phases               |
| 🗺️ Map Files       | `maps/final_map.yaml`, `maps/final_map.pgm`                                     | Final saved map generated from SLAM                  |
| ⚙️ Config Files     | `package.xml`, `CMakeLists.txt`                                                 | ROS package configuration files                      |
| 🎥 Demo File        | `phase4_demo.bag` (via Google Drive link below)                                 | ROS bag recorded during final navigation             |
| 📦 Folder Structure | Properly organized ROS package folder tree                                      | See below                                            |

---

### 📁 Folder Structure

```
final_project_pkg/
├── CMakeLists.txt
├── include/
│   └── final_project_pkg/
├── launch/
│   ├── final_project.launch
│   ├── navigation.launch
│   └── slam.launch
├── maps/
│   ├── final_map.pgm
│   └── final_map.yaml
├── package.xml
├── src/
├── worlds/
│   ├── my_custom_world.world
│   └── turtlebot3_world.world
└── phase4_demo.bag (stored externally)
```

---

### 🎬 Video Demonstration

📹 **Demo Video (3 min)** → [Google Drive Link](https://drive.google.com/file/d/1rrEzlGXlTj9pJcZUV_AVFe4HSiz1NHY-/view?usp=sharing)
🎒 **ROS Bag File (.bag)** → [Google Drive Link](https://drive.google.com/file/d/1Ve0Dgjna5cCT206hdfj0KyPSfdnC895K/view?usp=sharing)


---

### ⚙️ How to Run the Project

#### **1️⃣ Launch Gazebo (Phase 1 – Simulation World)**

```bash
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

#### **2️⃣ Run SLAM to Build Map (Phase 2)**

```bash
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
rosrun turtlebot3_teleop turtlebot3_teleop_key
```

Use keyboard teleop (`W`, `A`, `S`, `D`) to move the robot around and generate a map.
When mapping is complete, save the map:

```bash
rosrun map_server map_saver -f ~/final_project_ws/src/final_project_pkg/maps/final_map
```

#### **3️⃣ Navigation using Saved Map (Phase 3)**

```bash
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=/home/megge/final_project_ws/src/final_project_pkg/maps/final_map.yaml
```

Use RViz to:

* Click **2D Pose Estimate** → set initial pose
* Click **2D Nav Goal** → send navigation target

#### **4️⃣ Record the Navigation Demo (Phase 4)**

```bash
rosbag record -O phase4_demo.bag /odom /amcl_pose /move_base/status /scan
```

Stop recording with `Ctrl + C`.

---

### 🧾 Key Features

✅ Autonomous localization and navigation
✅ GUI-based simulation (not headless)
✅ SLAM mapping with GMapping
✅ Costmap-based global and local path planning
✅ Organized package structure

---

### 🧠 Future Enhancements

* Integrate obstacle avoidance using LiDAR data
* Implement dynamic path planning algorithms (e.g., D*, A*)
* Deploy to a physical TurtleBot3

---

### 🛡️ Notes

* `.bag` file and `.mp4` video are uploaded to Google Drive to avoid GitHub size limits.
* All launch files and map files are functional and verified through simulation.
* The system runs on ROS Noetic under WSL Ubuntu with built-in GUI rendering.

---

