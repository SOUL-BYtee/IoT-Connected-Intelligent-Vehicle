# IoT-Connected Intelligent Vehicle

Graduation project, Faculty of Engineering, Zagazig University. Supervised by Dr. Azhar.

An intelligent ground vehicle with autonomous navigation built on ROS 2 and Nav2,
simulated in Gazebo, with an IoT link (MQTT / EMQX) for remote monitoring and control.


## Contents

- [Project overview](#project-overview)
- [Data Engineering](#data-engineering)
- [ROS 2](#ros-2)
- [Embedded Systems](#embedded-systems)
- [Cloud](#cloud)
- [Hardware](#hardware)
- [Team workflow](#team-workflow)

## Project overview

The vehicle senses its surroundings, plans a path and drives itself. Four layers work together:

| Layer | Team | What it does |
| --- | --- | --- |
| Navigation and simulation | ROS 2 | Robot model, Gazebo, Nav2, goal sending |
| Low-level control | Embedded Systems | STM32 firmware that drives motors and reads sensors |
| Connectivity and storage | Cloud | MQTT broker (EMQX) and cloud services for telemetry |
| Data | Data Engineering | Pipelines that collect, process and store vehicle data |
| Physical build | Hardware | Chassis, lidar, encoders, IMU and power |

Overall roadmap:

- [x] ROS 2 workspace and environment setup
- [x] Robot model (URDF / xacro)
- [x] Gazebo simulation + RViz visualization
- [ ] Nav2 navigation stack (in progress)
- [ ] STM32 bridge node
- [ ] MQTT telemetry to EMQX
- [ ] Single package + one launch file
- [ ] Hardware phase: chassis, lidar, encoders and IMU selection

---

<!-- ===================== DATA ENGINEERING TEAM ===================== -->
<!-- Only the Data Engineering team edits between this marker and the next. -->

## Data Engineering

### About this section

Owned by the Data Engineering team. Replace this paragraph with what the team is responsible for in the project (for example: which data the vehicle produces, how it is collected, processed and stored).

### Progress and work done

_Nothing added yet. The team adds finished work, diagrams, setup steps and links here._

---

<!-- ===================== ROS 2 TEAM ===================== -->
<!-- Only the ROS 2 team edits between this marker and the next. -->

## ROS 2

### About this section

Owned by the ROS 2 team. Responsible for the robot model, the Gazebo simulation, RViz visualization and the Nav2 autonomous navigation stack.

### Repository structure

```
ros2/
  models/    Robot description: URDF + xacro sources (my_robot)
  launch/    Launch files: RViz viewer and Gazebo simulation
  config/    ros_gz bridge configuration
  maps/      Occupancy grid map for Nav2 (pgm + yaml)
  scripts/   Helper scripts (Nav2 goal sender)
```

### Requirements

- ROS 2 with Nav2 and xacro
- Gazebo Sim with ros_gz (`ros_gz_sim`, `ros_gz_bridge`)
- RViz and `joint_state_publisher_gui` for the viewer

### Quick start

Clone the repository, then from the repository root.

View the robot in RViz:

```bash
ros2 launch ros2/launch/view_robot.launch.py
```

Run the Gazebo simulation:

```bash
ros2 launch ros2/launch/gazebo_robot.launch.py
```

Send a navigation goal (with Nav2 running):

```bash
python3 ros2/scripts/goal.py 1.0 0.5
```

The launch files resolve their paths relative to the repository, so they work
from any clone location.

### Progress

- [x] Step 1: Workspace and environment setup
- [x] Step 2: Robot model (URDF / xacro)
- [x] Step 3: Gazebo simulation + RViz visualization
- [ ] Step 4: Nav2 navigation stack (in progress)
- [ ] Step 5: STM32 bridge node
- [ ] Step 6: MQTT telemetry to EMQX
- [ ] Step 7: Single package + one launch file

---

<!-- ===================== EMBEDDED SYSTEMS TEAM ===================== -->
<!-- Only the Embedded Systems team edits between this marker and the next. -->

## Embedded Systems

### About this section

Owned by the Embedded Systems team. Replace this paragraph with what the team is responsible for (for example: the STM32 firmware, motor control, sensor reading and the link to the ROS 2 side).

### Progress and work done

_Nothing added yet. The team adds finished work, pin maps, wiring notes and build instructions here._

---

<!-- ===================== CLOUD TEAM ===================== -->
<!-- Only the Cloud team edits between this marker and the next. -->

## Cloud

### About this section

Owned by the Cloud team. Replace this paragraph with what the team is responsible for (for example: the MQTT broker on EMQX, cloud services and remote monitoring and control).

### Progress and work done

_Nothing added yet. The team adds finished work, architecture notes and setup steps here._

---

<!-- ===================== HARDWARE TEAM ===================== -->
<!-- Only the Hardware team edits between this marker and the next. -->

## Hardware

### About this section

Owned by the Hardware team. Replace this paragraph with what the team is responsible for (for example: chassis, lidar, encoders, IMU, motors and power).

### Progress and work done

_Nothing added yet. The team adds the parts list, schematics, photos and build notes here._

---

## Team workflow

1. Create a branch for your change: `git checkout -b feature/my-change`
2. Edit only your own team's section of this README, and only your team's folders.
3. Commit and push your branch.
4. Open a pull request into `main` and ask a teammate for review.
5. Keep `main` runnable: do not merge broken launch files or models.
