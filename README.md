# Stability Control System
A high-fidelity cart-pole simulation using RK4 integration and a non-linear control law to stabilize a 9-degree initial perturbation.


### A Study in Disturbance Rejection and Asymmetric Control

![Activestabilityproject-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/2710f90b-f7c4-48b1-91a9-ad20caa7248f)


## Project Overview
This project implements a physics simulation of the classic Inverted Pendulum (Cart-Pole) problem. The goal was to design a robust controller capable of stabilizing the pole from a 9 to 10-degree initial tilt while maintaining the cart within a constrained 4-meter track.
<img width="1803" height="1140" alt="Screenshot 2026-03-29 042748" src="https://github.com/user-attachments/assets/2bacdd32-7555-4c57-ac84-35f8fb588398" />

Fig 1: Real-time stabilization of a 9-degree initial perturbation.

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

## 📊 Current Performance Benchmarks
* **Long-Duration Stability:** Successfully maintained vertical equilibrium for **>150 seconds** without numerical drift.
* **Station-Keeping Envelope:** Implemented a restorative bias that constrains the airframe within a **±2m lateral boundary** from the origin.
* **Numerical Precision:** Utilized **4th-Order Runge-Kutta (RK4)** integration to ensure energy conservation, crucial for high-fidelity aerospace modeling.
<img width="1804" height="1149" alt="image" src="https://github.com/user-attachments/assets/4e4df751-0f6e-4033-a9b4-cd93d325c527" />
Figure 2: Long-Duration Stability & Constraint Handling. Telemetry at T+152.0s demonstrating zero steady-state angular error (Theta = 0°). The controller successfully maintains Station-Keeping within the operational envelope (+1.80m), proving robust recovery and stability near the physical track boundaries—a critical requirement for both autonomous robotics and UAV flight-guards.

---

## How to Run
1. Ensure you have numpy and matplotlib installed:
   pip install numpy matplotlib
2. Run the simulation

---
## 🛠 Active Research & Future Iterations
* **Stochastic Disturbance Rejection:** Currently developing a module to inject periodic 50N impulses to simulate atmospheric turbulence and "wind gusts."
* **Recovery Analysis:** Evaluating the controller's "Time-to-Recovery" following 10-degree upset conditions under active disturbance.
* **3D Proxy Mapping:** Planning a transition from 2D Cart-Pole logic to 3D Quadcopter altitude-hold dynamics.
---
