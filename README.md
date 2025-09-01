# Heat Exchanger Simulation

A Python GUI application to simulate and visualise counter-current and co-current heat exchangers. This tool allows users to explore how hot and cold fluid streams exchange heat along a heat exchanger and see the results in temperature profiles and pipe schematics.

---

## Features

- Counter-current and co-current configurations
- Input parameters for:
  - Hot/cold inlet temperatures
  - Mass flow rates
  - Heat capacities
  - Overall heat transfer coefficient
  - Heat exchanger area and length
- Real-time visualisation:
  - Temperature vs. position plot
  - Colored pipe schematic representing hot and cold streams
  - Calculates the outlet temperatures of both streams
- Interactive Tkinter GUI to update parameters 

---
# Technical Background

This project simulates a double-pipe heat exchanger in both counter-current and co-current flow configurations. The model is based on solving the coupled differential energy balances for the hot and cold streams along the exchanger length.

**Governing Equations**

Hot stream:
dTh/dx = -(U * dA/dx) / (m_h * cp_h) * (Th - Tc)

Cold stream:
dTc/dx = (U * dA/dx) / (m_c * cp_c) * (Th - Tc) **(with a nagative sign for counter-current)**

where:
U    = overall heat transfer coefficient [W/m²·K]  
A    = heat transfer area [m²]  
L    = heat exchanger length [m]  

m_h  = hot stream mass flow rate [kg/s]  
cp_h = hot stream specific heat capacity [J/kg·K]  
Th   = hot stream temperature [°C]  
Th_in = hot stream inlet temperature [°C]  

m_c  = cold stream mass flow rate [kg/s]  
cp_c = cold stream specific heat capacity [J/kg·K]  
Tc   = cold stream temperature [°C]  
Tc_in = cold stream inlet temperature [°C]  

x    = length coordinate along exchanger [m]  

**Boundary Conditions**

Co-current (both enter at x=0)
Th(0) = Th_in
Tc(0) = Tc_in

Counter-current (hot stream enter at x=0, cold stream at x=L)
Th(0) = Th_in
Tc(L) = Tc_in

**Numerical Method**

For co-current flow (both conditions at x=0), the problem is an Initial Value Problem (IVP), 
which can also be solved using odeint.

Because one set of boundary conditions is specified at each end in the counter-current case, 
the problem becomes a Boundary Value Problem (BVP).
SciPy’s solve_bvp is used to solve the coupled ODEs.

An initial guess for hot and cold temperature profiles is provided (a linear interpolation in this case).
The solver iterates until the residuals in the boundary conditions fall below tolerance.

**Results & Visualisation**

The solver returns temperature profiles.
These are plotted against the exchanger length to show the temperature variation.

In addition, the profiles are mapped onto coloured cylinders representing the hot and cold pipes, 
with a temperature colourmap for intuitive visualszation.

Counter-current exchangers typically achieve a greater temperature change in the cold stream 
and higher effectiveness.
Co-current exchangers have a steeper gradient at the inlet but a smaller mean temperature difference overall.

---

# Installation
Clone this repository and install required packages. Run this in your terminal:

```bash
git clone https://github.com/minangajayasekera-ops/Heat_exchanger_GUI.git
cd Heat_exchanger_GUI
pip install -r requirements.txt

```

**Dependencies**
- Python 3.8+
- NumPy
- Matplotlib
- Scipy
- Tkinter (usually comes with Python)
- Jupyter Notebook

**Usage**
- Launch Jupyter Notebook in your terminal:
```
jupyter notebook
```
- Then open Heat_exchanger_GUI.ipynb and run the code.
- When the Tkinter GUI pops up input your values and select your configuration.
- Click "update plot" to see the temperature profiles with the schematic of the pipes.

---

# Future Improvements 
- Including NTU-effectiveness
- Transient (unsteady state) behaviour
- Other arrangements like Shell and Tube heat exchangers


Developed by **Minanga Jayasekera**
First-year Chemical Engineering student @ Imperial College London

