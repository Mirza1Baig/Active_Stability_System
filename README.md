# Inverted_Pendulum_Control
A high-fidelity cart-pole simulation using RK4 integration and a non-linear control law to stabilize a 9-degree initial perturbation.


### A Study in Disturbance Rejection and Asymmetric Control
<img width="1803" height="1140" alt="Screenshot 2026-03-29 042748" src="https://github.com/user-attachments/assets/2bacdd32-7555-4c57-ac84-35f8fb588398" />

Fig 1: Real-time stabilization of a 9-degree initial perturbation.

## Project Overview
This project implements a physics simulation of the classic Inverted Pendulum (Cart-Pole) problem. The goal was to design a robust controller capable of stabilizing the pole from a 9 to 10-degree initial tilt while maintaining the cart within a constrained 4-meter track.

### Key Engineering Challenges:
- Non-Linear Dynamics: Handling disturbances beyond small-angle approximations.
- Track Constraint Management: Balancing restorative force against physical track limits.
- Numerical Stability: Implementing higher-order integration to prevent energy gain.


## Technical Implementation

### 1. Physics Engine (RK4 Integration)
Unlike simple Euler integration, this simulation uses a 4th-order Runge-Kutta (RK4) method. This ensures that the energy of the pendulum is conserved and that the simulation remains stable even at high-frequency control updates (dt = 0.006s).

### 2. Control Strategy
The system utilizes a custom Asymmetric Proportional-Derivative (PD) control law. 
- Feather Balancing: The torque output is scaled by a non-linear power function of the sine of the angle to provide more aggressive correction.
- Asymmetric Centering Bias: To prevent long-term lateral drift, a position-dependent bias is applied. 
- Damping Schedule: Specific derivative gains were tuned to minimize settling time.

---

## Performance Analysis
- Settling Time: Approximately 3.5 seconds.
- Disturbance Rejection: Recovered from a 10-degree initial offset.
- Steady-State Error: Minimized positional drift within 5% of track center.

---

## How to Run
1. Ensure you have numpy and matplotlib installed:
   pip install numpy matplotlib
2. Run the simulation

---
