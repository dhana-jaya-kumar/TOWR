# TOWR
A Simulation Test Bed in PyBullet physics engine for Trajectory Optimizer for Walking Robots (TOWR)
<p align="center">
   <img width="260" height="280" src="https://github.com/lok-i/towr_pybullet/blob/master/media/stairs.gif">
   <img width="260" height="280" src="https://github.com/lok-i/towr_pybullet/blob/master/media/turn.gif">
   <img width="260" height="280" src="https://github.com/lok-i/towr_pybullet/blob/master/media/trot.gif">
</p>

<p align = "center">
<i>Climbing Stairs(left), Turning about the axis(centre), Trotting to a given target(right) </i><br>
</p>

## Introduction:
The growing field of *Robot Learning* requires faster prototyping and flexible simulation arrangments to incorprate various learning based frameworks.The arrival of modules like *Tensorflow,Pytorch* for learning and *Pybullet* for simulation has made *Python*, a very attractive choice for training and testing learning based agents in robots.This codebase is an attempt to build a pythonic wrapper arround **TOWR - Trajectory Optimizer for Walking Robots**(https://github.com/ethz-adrl/towr).

## TOWR:
<p align="center">
   <img width="700" height="400" src="https://github.com/lok-i/towr_pybullet/blob/master/media/towr.gif">
</p>

**TOWR(Trajectory Optimizer for Walking Robots)**, is a state of the art light-weight and extensible C++ library for trajectory optimization for legged robots developed in **ETH Zurich** by **Alexander Winkeler** and his team.It proposes to address the problem of integrated motion planning as a non-linear optimization problem and there by provides a deasible kinematics solution.This framework is very versatile as address the robot's constraints (from its dynamic and kinematic model),the world constraints and the goal constraints.Having been tested across various terrain, robots,and gait types it also allows the users to import their own robot model or add custom constraints and terrain models.

## Our Work:

TOWR is entirely developed in C++ and has inbuilt support to visualize the generated trajectories.However, there is no available code for using TOWR with a physics simulator.Their paper shows the validation of towr in Gazebo, which requires
the usage additional ROS packages.This is quite cumbersome and not very straightforward for the robot learning community givent the ease that *Pybullet* provides us with.In the repo, we have built python functions to visualize aswell as simulate the TOWR generated trajectories on the robot platform ANYmal with different gait types and multiple terrains(flat ground and stairs as of now)


**Note:**

* The **Green Robot** is a Visual robot that has no incorprated physics but just act as a visual aid to display the ideal TOWR generated trajectories.
* The **Grey Robot** is the real physical robot model (with mass and inertia) in which the computed joint angles (corresponding to the TOWR trajectory) are applied.
* In the above simulation, **TOWR trajectories where recomputed until the real robot(grey) reaches the desired target taking the current position and orientation of the real robot as initial state**.
* The above results are pure **Position Control** and the **Feet Contact force** given out by TOWR has not been utilized yet.
* From our experiments it is clearly visible(from the failures of the grey robot) that the TOWR trajectories are not directly deployable in a robot and requires a control strategy that could bridge the reality gap.
