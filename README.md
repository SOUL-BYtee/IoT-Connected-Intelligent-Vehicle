# IoT-Connected Intelligent Vehicle

Graduation project, Faculty of Engineering, Zagazig University.

An intelligent ground vehicle with autonomous navigation built on ROS 2 and Nav2,
simulated in Gazebo, with an IoT link (MQTT / EMQX) for remote monitoring and control.

This is the team repository: every member pushes their work here. See
[Team workflow](#team-workflow) before your first commit.

## Project roadmap

ROS 2 bring-up, step by step:

- [x] Step 1: Workspace and environment setup
- [x] Step 2: Robot model (URDF / xacro)
- [x] Step 3: Gazebo simulation + RViz visualization
- [ ] Step 4: Nav2 navigation stack (in progress)
- [ ] Step 5: STM32 bridge node
- [ ] Step 6: MQTT telemetry to EMQX
- [ ] Step 7: Single package + one launch file

Phase 2 (hardware): chassis, lidar, encoders and IMU selection.

## Repository structure

```
ros2/
  models/    Robot description: URDF + xacro sources (my_robot)
  launch/    Launch files: RViz viewer and Gazebo simulation
  config/    ros_gz bridge configuration
  maps/      Occupancy grid map for Nav2 (pgm + yaml)
  scripts/   Helper scripts (Nav2 goal sender)
```

## Requirements

- ROS 2 with Nav2 and xacro
- Gazebo Sim with ros_gz (`ros_gz_sim`, `ros_gz_bridge`)
- RViz and `joint_state_publisher_gui` for the viewer

## Quick start

Clone the repository, then from the repository root:

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

## Team workflow

1. Create a branch for your change: `git checkout -b feature/my-change`
2. Commit and push your branch.
3. Open a pull request into `main` and ask a teammate for review.
4. Keep `main` runnable: do not merge broken launch files or models.

## Supervision

Supervised by Dr. Azhar.
