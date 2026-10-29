# CaminoSantigoSXII
3D route modeling and milestone calculation using parametric cubic splines in Python. Integrates numerically to measure path distances and applies the Newton-Raphson method to place equidistant markers along historical paths (e.g., Camino de Santiago).

# 3D Route Modeling & Milestone Calculation (Cubic Splines)

A Python program designed to model 3D geographical routes using parametric natural cubic splines. It calculates the total length of the curve by integrating the spline polynomials segment by segment and uses numerical methods to place equidistant milestones along the path. 

This project was originally developed to model a 12th-century horseback route along the **Camino de Santiago** (from Jaca to Santiago de Compostela), calculating realistic daily travel distances between historical churches and monasteries.

## Features

- **3D Spline Interpolation:** Reads discrete UTM coordinates and generates natural cubic splines for the X, Y, and Z axes using `scipy.interpolate.CubicSpline`.
- **Numerical Derivation & Integration:** Computes spatial derivatives using central finite differences and calculates exact path lengths using SciPy's `quad` integration.
- **Root Finding:** Employs the **Newton-Raphson** algorithm to determine the exact parameter $t$ for equidistant physical milestones (e.g., every 1 km).
- **Interactive 3D Visualization:** Plots the topographic route in a 3D Matplotlib projection, rendering the path, highlighting the specified cities/stops, and mapping the calculated milestones.

## Project Structure

| File | Description |
|---|---|
| `principal.py` | Main entry point. Interactive CLI to configure the scale, load data, and run the calculations. |
| `lee_camino.py` | Reads the coordinate file and generates the 3D natural cubic splines. |
| `kilometra_camino.py` | Core algorithm: Uses Newton-Raphson to place equidistant milestones along the path. |
| `longitud_camino.py` | Calculates total or partial path lengths via numerical integration. |
| `dlong.py` & `derivada.py` | Computes the differential length $dl = \sqrt{dx^2 + dy^2 + dz^2}$ and spatial derivatives using finite differences. |
| `punto_camino.py` | Evaluates the X, Y, Z coordinates on the spline for any given parameter $t$. |
| `dibuja_camino.py` | Handles the 3D visualization of the route and city labels using Matplotlib. |
| `tabla_kilometros.py` | Prints a formatted tabular summary of the calculated milestones to the console. |
| `dibuja_hitos.py` | *(Dependency referenced in main)* Adds the calculated milestone markers to the 3D plot. |

## Installation

```bash
git clone [https://github.com/YOUR_USER/YOUR_REPOSITORY.git](https://github.com/YOUR_USER/YOUR_REPOSITORY.git)
cd YOUR_REPOSITORY
pip install -r requirements.txt
