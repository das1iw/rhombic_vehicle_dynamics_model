# Rhombic Vehicle Nonlinear Dynamics Model

Nonlinear rhombic vehicle dynamics model implemented in MATLAB/Simulink based on:

Huang Zhi, Zhong Zhihua
Analysis of Steering Dynamics of Rhombic New Concept Car

⸻

## Features

* Nonlinear coupled vehicle body dynamics
* Yaw-roll coupling
* Pacejka tire model
* Dynamic vertical load transfer
* Front and rear steering
* Rhombic wheel configuration
* Fully signal-based Simulink implementation
* Suitable for controller development, AV research, and nonlinear vehicle dynamics analysis.

⸻

## Vehicle Configuration

The vehicle uses a rhombic wheel layout:

* 1 front wheel
* 2 middle wheels
* 1 rear wheel

The middle wheels are responsible for lateral load transfer.

⸻

## Dynamic States

The model includes:

* Longitudinal velocity vx
* Lateral velocity vy
* Yaw rate r
* Roll angle phi
* Roll rate phi_dot
* Wheel angular velocities w1 w2 w3 w4

⸻

## Vehicle Dynamics Equations

<img width="373" height="338" alt="Screenshot 2026-05-12 at 12 31 30" src="https://github.com/user-attachments/assets/d23d3821-fc3d-458a-918c-a39ca1797f52" />


The coupled nonlinear equations are solved simultaneously using matrix inversion.

⸻

## Tire Model

The tire forces are generated using the nonlinear Pacejka tire model.

For each wheel:

* longitudinal force Fx
* lateral force Fy

are computed from:

* slip ratio
* slip angle
* vertical load

⸻

## Dynamic Vertical Loads

Dynamic wheel loads are calculated separately.

The rhombic configuration assumes:

* front and rear wheels lie on the centerline
* middle wheels carry lateral load transfer

A Memory block is used in Simulink to avoid algebraic loops caused by:

* tire force feedback
* vertical load feedback
* lateral acceleration coupling

⸻

## Initial Conditions

Initial Longitudinal Speed

v_{x0}=5\ m/s

This value is assigned as the initial condition of the longitudinal velocity integrator.


Initial wheel angular velocity is computed from the pure rolling condition:

\omega_0=\frac{v_{x0}}{R_w} (10)

where:

* Rw = wheel radius

This ensures:

* zero initial slip ratio
* numerically stable startup conditions

⸻

## Notes

* All parameters are implemented as Simulink input signals
* No constants are declared inside MATLAB Function blocks
* Vehicle parameters must be initialized beforehand by running: vehicle_params.m
* The model is fully modular and signal-based
* No controllers are used
* Td (driving torque) and Tb (braking torque) are zero
* Suitable for:
    * MPC
    * Reinforcement Learning
    * Torque Vectoring
    * Stability Control
    * Autonomous Vehicle Research
    * Nonlinear Vehicle Dynamics Analysis

⸻

Reference

Huang Zhi, Zhong Zhihua,
Analysis of Steering Dynamics of Rhombic New Concept Car,
Journal of Hunan University, 2006.

Copyright (c) 2026 Dastan

