# F1 Tenth Simulator:
This repository primarily consists of a simulator for the F1-tenth vehicle built in Gazebo by MIT and further modified by UPenn to drive around autonomously using techniques such as wall following and  pure-pursuit. This has been tested on Gazebo 7.16.0 in Ubuntu 16.04 with ROS Kinetic installed. The simulated vehicle has a Hokuyo LIDAR with 270 degrees FOV and a ZED camera as its on-board sensors. It also has an IMU and odometry estimation obtained from the [VESC](https://electric-skateboard.builders/t/new-vesc-user-read-this-complete-walktrough-of-the-vesc/2980).

![Alt Text](./images/output.jpeg)



Instructions to Install:
---

Assuming you have ROS and Gazebo installed run:

```$ sudo apt-get install ros-kinetic-ros-control ros-kinetic-ros-controllers ros-kinetic-gazebo-ros-control ros-kinetic-ackermann-msgs ros-kinetic-joy```

To install the navigation packages run the following:

```$ sudo apt-get install ros-kinetic-teb-local-planner ros-kinetic-move-base ros-kinetic-navigation ros-kinetic-driver-base```

The package should be cloned somewhere in the `src` in a catkin_workspace. To clone the package run:

```$ git clone .....TODO```

To launch the simulation run the following command: `roslaunch race f1tenth.launch`



Vehicle Characteristics:
---

| Velocity       | Full Left | Straight | Full Right |
| :------------- | --------- | -------- | ---------- |
| Steering value | -0.5      | 0        | 0.5        |

While using it to test an external controller, the control commands are to be issued on the topic:

`/vesc/ackermann_cmd_mux/input/teleop`

Speed is supposed to be published on `msg.drive.speed` and steering angle is to be published on `msg.drive.steering_angle` where `msg` is an `AckermannDriveStamped` message.

If these bounds are crossed, the steering geometry distorts to unrealistic angles, hence they have to be limited in the external controller itself.



Special Note
---
This simulator was build by teams at MIT to drive a car using keyboard buttons and was modified to drive the car autonomously.
