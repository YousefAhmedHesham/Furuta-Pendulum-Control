# Furuta Pendulum: Rotary Inverted Pendulum Control 🔄⚖️

![MATLAB](https://img.shields.io/badge/MATLAB-R2023b-orange) ![Simulink](https://img.shields.io/badge/Simulink-Control-blue) ![Topic](https://img.shields.io/badge/Topic-Pole%20Placement-green) ![Status](https://img.shields.io/badge/Status-Completed-success)

## 📖 Project Overview
The control system design and simulation for a **Furuta Pendulum** (Rotary Inverted Pendulum). 
Developed as part of the **MCT411: Hybrid Control** course at **Ain Shams University**, the project aims to stabilize the underactuated pendulum in the upright position ($\theta_1 = 0$) using state-space control techniques.

The system consists of a driven arm (actuated by a DC motor) rotating in the horizontal plane and a pendulum rod (unactuated) attached to the arm, free to rotate in the vertical plane.

## 📺 Project Video
https://github.com/user-attachments/assets/22ef0341-d6d1-43d0-a15a-679fcaaeca6f



## 🎨 CAD Renders
Below are visualizations of the mechanical design
<img width="1920" height="881" alt="iso2" src="https://github.com/user-attachments/assets/76e1f052-838a-4a47-bc55-d6537b40c56d" />
<img width="1920" height="881" alt="iso" src="https://github.com/user-attachments/assets/88680612-c7d1-4d97-8899-a0b355d9943e" />


## ⚙️ Control Strategy
The control system is designed to stabilize the pendulum and reject external disturbances.

### 1. Mathematical Modeling
The non-linear system is linearized around the upright equilibrium point. The parameters used in `Furuta_Constants.m` are:
* **Arm Mass ($m_1$):** 0.03217 kg
* **Pendulum Mass ($m_2$):** 0.038 kg
* **Arm Length ($L_1$):** 0.095 m
* **Pendulum Length ($L_2$):** 0.08 m
* **Motor Constants:** Back-EMF ($k_e$) = 0.967, Resistance ($R_e$) = 4.85 $\Omega$

### 2. State Feedback Control
We utilize **Pole Placement** to calculate the feedback gain matrix $K$.
* **Pseudo-Linearization:** A "Pseudo" state-space model ($A_p, B_p$) is constructed in MATLAB to handle the system dynamics.
* **Controllability:** The system is verified to be controllable (`rank(ctrb(Ap,Bp))`) before computing gains.

## 📂 Repository Structure
* `furutaaa.slxc` - Simulink cache/model file containing the control loop.
* `Furuta_Constants.m` - Initialization script. Defines physical constants ($g, m1, L1, J$) and calculates the State Feedback controller.
* `CAD/` - (Optional) 3D design files for the mechanical assembly.

## 🚀 How to Run
1.  **Prerequisites:** MATLAB & Simulink (R2023b or later recommended).
2.  **Setup:**
    * Open `Furuta_Constants.m` in MATLAB.
    * Run the script to load the workspace variables ($A, B, C, K$ matrices).
3.  **Simulation:**
    * Open the Simulink model (linked to `furutaaa.slxc`).
    * Run the simulation to observe the arm regulating the pendulum angle to $0^\circ$.
