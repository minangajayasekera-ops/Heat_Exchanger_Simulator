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
