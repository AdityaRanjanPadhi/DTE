# Dynamic Tilt Estimation for Pen Tracking Using a Single Tri-Axial Accelerometer

MATLAB implementation of the dynamic tilt estimation framework presented in:

> **Aditya Ranjan Padhi**
> *Dynamic Tilt Estimation for Pen Tracking Using a Single Tri-Axial Accelerometer*

---

## Abstract

Accurate trajectory reconstruction using inertial sensors requires the removal of gravitational acceleration from the measured accelerometer signals. During handwriting, continuous changes in pen orientation cause the gravity vector to project onto multiple sensor axes, making direct integration unreliable. This challenge is commonly referred to as the **dynamic tilt problem**.

This repository presents a constrained optimization framework for estimating the roll and pitch angles of a pen-mounted accelerometer using only tri-axial acceleration measurements. The proposed method combines:

* Gravity constraints
* Planar writing constraints
* Rodrigues rotation formulation
* Temporal continuity constraints

The estimated orientation enables gravity compensation, providing a foundation for inertial trajectory localization and digital handwriting applications.

---

## Features

* Dynamic tilt estimation using only accelerometer measurements.
* Constrained nonlinear optimization using `fmincon`.
* Temporal consistency constraints.
* Rodrigues rotation formulation.
* Monte Carlo simulation support.
* MATLAB implementation with equation-to-code correspondence.
* Reproducible simulation results.

---

## Repository Structure

```text
.
├── Main.m
├── Simulink_Model.slx
├── Dataset/
│   ├── Circular_Motion/
│   ├── Straight_Line_Motion/
│   └── Eight_Motion/
└── README.md
```

---

## Requirements

* MATLAB R2024b (tested)
* Optimization Toolbox
* Simulink (for generating motion data)

---

## Running the Code

Open:

```matlab
Main.m
```

Specify the motion file:

```matlab
FILEPATH = "Results\Circular_Motion\results_err_0_seed_1.mat";
```

Run the script:

```matlab
run('Main.m')
```

The program estimates:

* Pitch angle ((\theta))
* Roll angle ((\phi))

and generates plots comparing:

* Estimated orientation
* Ground truth orientation
* Estimation error

---

## Methodology

The proposed framework formulates tilt estimation as a constrained optimization problem.

The optimization combines:

1. Gravity constraint
2. Planar writing constraint
3. Temporal continuity constraint

The implementation directly corresponds to the equations presented in the accompanying publication.

| Equation | MATLAB Implementation |
| -------- | --------------------- |
| Eq. (1)  | `fax`                 |
| Eq. (2)  | `fay`                 |
| Eq. (3)  | `faz`                 |
| Eq. (7)  | `alpha`               |
| Eq. (8)  | `x_ang`               |
| Eq. (9)  | Projection constraint |
| Eq. (10) | Objective function    |

---

## Assumptions

The proposed method assumes:

1. The writing surface is parallel to the ground.
2. Yaw rotation is negligible.
3. The vertical acceleration is dominated by gravity.
4. Pen orientation changes smoothly over time.

These assumptions are consistent with typical handwriting motion.

---

## Example Results

The framework produces:

* Estimated roll angle
* Estimated pitch angle
* Error plots
* Monte Carlo performance analysis

Representative results are shown in the accompanying publication.

---

## Citation

If you use this code in your research, please cite:

```bibtex
@article{padhi2026dynamic,
  author  = {Aditya Ranjan Padhi},
  title   = {Dynamic Tilt Estimation for Pen Tracking Using a Single Tri-Axial Accelerometer},
  year    = {2026}
}
```

---

## Author

**Aditya Ranjan Padhi**
Signal Processing and Communications Research Center (SPCRC)
Indian Institute of Information Technology Hyderabad

---

## License

This software is provided for academic and research purposes.

Copyright © 2026 Aditya Ranjan Padhi.

---

## Future Work

This work forms the first stage of the **Pankh** inertial pen-tracking framework.

Future developments include:

* Gravity compensation
* Trajectory localization
* Multi-model filtering
* Hardware implementation
* Real-time digital handwriting systems
