# Airfoil Performance Simulator

A Python/Jupyter Notebook project for exploring the aerodynamic behavior of NACA 4-digit airfoils.

I built this project as a computational companion to a subsonic wind tunnel project. The goal is to connect basic aerodynamic theory with a tool that visualizes how airfoil geometry, angle of attack, airspeed, and Reynolds number affect performance.

## Features

The notebook can:

- generate NACA 4-digit airfoil geometry
- calculate Reynolds number
- estimate zero-lift angle
- estimate lift coefficient
- estimate drag coefficient
- calculate lift and drag forces
- visualize lift coefficient vs. angle of attack
- estimate pressure distribution over the airfoil
- estimate surface velocity distribution
- show qualitative stall behavior
- examine Reynolds number effects on drag

## Example Inputs

```text
NACA airfoil: 2412
Angle of attack: 5 degrees
Air speed: 20 m/s
Chord length: 0.30 m
Reference span: 0.50 m
```

## Example Outputs

For a NACA 2412 airfoil at the default conditions, the notebook produces values such as:

```text
Reynolds number:      ~406,000
Lift coefficient:     ~0.78
Drag coefficient:     ~0.011
```

It also generates plots of the airfoil geometry, lift curve, pressure distribution, surface velocity, and Reynolds-number effects.

## Aerodynamics

### Reynolds Number

The Reynolds number is calculated using:

```text
Re = rho * V * c / mu
```

where:

- `rho` is air density
- `V` is freestream velocity
- `c` is chord length
- `mu` is dynamic viscosity

### Lift

Before stall, lift is estimated using thin-airfoil theory:

```text
Cl = 2*pi*(alpha - alpha_zero_lift)
```

where the angle is measured in radians.

The zero-lift angle is estimated from the NACA mean camber line, allowing cambered airfoils such as NACA 2412 to behave differently from symmetric airfoils such as NACA 0012.

### Pressure Coefficient

Pressure coefficient is estimated using:

```text
Cp = 1 - (V_surface / V_infinity)^2
```

The surface velocity distribution comes from a simplified thin-airfoil circulation model.

### Stall and Drag

Thin-airfoil theory does not directly model flow separation or stall. This project adds a simplified post-stall correction to show the general trend in lift.

Drag is also estimated using a simplified model that combines skin friction, airfoil thickness effects, lift-related drag, and an additional post-stall penalty.

These values are intended for educational and trend analysis rather than high-fidelity aerodynamic prediction.

## Project Structure

```text
airfoil-performance-simulator/
├── airfoil_performance_simulator.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/airfoil-performance-simulator.git
cd airfoil-performance-simulator
```

Install the required Python packages:

```bash
pip install -r requirements.txt
```

Then open the notebook:

```bash
jupyter notebook airfoil_performance_simulator.ipynb
```

You can also open it directly in VS Code or JupyterLab.

## Requirements

- Python 3
- NumPy
- Matplotlib
- Jupyter

## Limitations

This project is not a CFD solver.

It does not fully model:

- turbulence
- viscous flow separation
- exact stall angle
- three-dimensional wingtip effects
- compressibility
- transonic or supersonic flow

The drag and stall models are simplified approximations intended to show aerodynamic trends.

## Future Improvements

Some possible next steps are:

- compare predictions with experimental wind tunnel data
- import measured data from CSV files
- compare theoretical and experimental lift curves
- add Arduino sensor data from the wind tunnel
- support more airfoil families
- implement a panel method
- compare results with XFOIL
- add an interactive interface

## Motivation

This project was created to connect computational aerodynamics with hands-on wind tunnel work. The long-term goal is to compare theoretical predictions with experimental measurements from the physical wind tunnel.
