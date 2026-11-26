
# Particle Size Distribution, Crusher Efficiency, Drug Dissolution & Bioavailability

### Computational Modelling and Data Analysis | FMO Mini Project (24BTEN2031)

**Domain:** Biotechnology | Pharmaceutical Engineering | Computational Modelling | Data Analytics

**Institution:** GITAM (Deemed to be University), Department of Biotechnology

---

## 1. Project Overview

Particle Size Distribution (PSD) is an important physical property influencing the dissolution behaviour of pharmaceutical powders. For poorly water-soluble drugs, reducing particle size can increase the available surface area, potentially improving dissolution rates and drug absorption.

However, particle size reduction also introduces engineering challenges involving energy consumption, crusher efficiency, powder handling and manufacturing consistency.

This project investigates the relationship between particle size distribution, size-reduction processes, dissolution kinetics and simulated bioavailability through a combination of mathematical modelling, Python-based computational simulations and quantitative data analysis.

The project extends beyond theoretical interpretation by implementing computational models to generate, process, compare and visualize simulated datasets.

**Important:** All computational results are simulated using mathematical models and illustrative assumptions. They are not experimental measurements or clinically validated predictions.

---

## 2. Problem Statement

Pharmaceutical powders require controlled particle size distributions to achieve consistent dissolution behaviour and product quality.

Although reducing particle size generally increases specific surface area, the relationship between particle size and drug performance is not always linear. Excessive size reduction may increase energy requirements, promote particle aggregation and create manufacturing difficulties.

The central problem addressed in this project is:

**How can particle size distribution and size-reduction characteristics be computationally analysed to understand their influence on dissolution behaviour and simulated drug bioavailability?**

To investigate this, the project addresses four interconnected questions:

1. How do different size-reduction machines influence particle size distribution?
2. How do particle size and size-reduction requirements relate to energy consumption and crusher efficiency?
3. How can particle size distributions be mathematically characterized and evaluated?
4. How does changing particle size influence simulated dissolution profiles and pharmacokinetic parameters?

---

## 3. Project Objectives

- Model particle size distributions for different size-reduction machines.
- Calculate characteristic particle size descriptors, including D10, D50, D80 and D90.
- Estimate specific surface area using the Sauter mean diameter.
- Compare energy requirements using Kick's, Rittinger's and Bond's laws.
- Evaluate crusher efficiency using energy-based and surface-energy-based approaches.
- Simulate sieve analysis and evaluate Rosin–Rammler model fitting.
- Investigate the relationship between particle size and dissolution kinetics.
- Simulate drug absorption and plasma concentration profiles using a simplified pharmacokinetic model.
- Organize computational outputs into structured Excel datasets.
- Interpret the results in the context of pharmaceutical engineering and drug formulation.

---

## 4. Technical Implementation

The computational component was developed using Python, with NumPy, Pandas and Matplotlib for numerical calculations, data processing and visualization.

### 4.1 Particle Size Distribution Modelling

The Rosin–Rammler distribution was implemented to represent the cumulative mass fraction of particles finer than a given diameter.

The cumulative distribution is expressed as:

F(d) = 1 - exp[-(d/d')^n]

Where:

- F(d) = Cumulative mass fraction finer than particle diameter d.
- d = Particle diameter.
- d' = Characteristic size parameter.
- n = Distribution spread or uniformity parameter.

Five size-reduction machines were modelled:

- Jaw Crusher
- Roll Crusher
- Hammer Mill
- Ball Mill
- Jet (Fluid-Energy) Mill

The resulting distributions were used to calculate:

- D10, D50, D80 and D90
- Distribution span
- Sauter mean diameter (d32)
- Mass-mean particle diameter
- Specific surface area

Distribution span was calculated as:

Span = (D90 - D10) / D50

Specific surface area was estimated using:

S = 6 / (ρ × d32)

Where ρ represents particle density.

### 4.2 Energy Consumption and Crusher Efficiency

Three classical size-reduction energy models were implemented:

**Kick's Law**

E = K × ln(F/P)

**Rittinger's Law**

E = K × (1/P - 1/F)

**Bond's Law**

E = 10 × Wi × (1/√P - 1/√F)

Where:

- F = Feed particle size.
- P = Product particle size.
- K = Model-dependent constant.
- Wi = Bond work index.

Kick's and Rittinger's constants were calibrated to agree with Bond's model at a reference product size of 100 µm.

Crusher performance was evaluated using:

- Bond energy efficiency.
- Surface-energy efficiency.
- New surface area generated per unit energy consumed.

This enabled a comparative assessment of the theoretical energy requirements and assumed actual energy consumption of the five machines.

### 4.3 Simulated Sieve Analysis

A simulated 1 kg powder sample was evaluated using a sieve stack ranging from 16 mm to 25 µm, including a collection pan.

The simulation incorporated 2% random measurement noise.

The resulting datasets were used to:

- Calculate mass retained across sieve sizes.
- Determine mass fractions and cumulative passing percentages.
- Estimate particle size distribution parameters.
- Fit the Rosin–Rammler distribution.
- Compare sieve-derived estimates with the underlying simulated distributions.

The limitations of sieve analysis for very fine particles were also investigated, particularly when substantial material passes through the finest sieve.

### 4.4 Surface Area Modelling

The relationship between particle diameter and specific surface area was examined using:

S = 6 / (ρ × d)

The model illustrates the inverse relationship between particle diameter and specific surface area for spherical particles of constant density.

### 4.5 Drug Dissolution Modelling

A simplified dissolution model based on the Noyes–Whitney principle was implemented.

Particles were represented as spherical populations distributed across particle-size bins and modelled as shrinking during dissolution.

The simulation considered:

- Particle size distribution.
- Particle surface area.
- Diffusion coefficient.
- Saturation concentration.
- Diffusion-layer thickness.
- Gastrointestinal transit.
- Dissolution and absorption rates.

Dissolution behaviour was compared across selected machine-produced powders and four illustrative micronisation grades:

| Grade | Assumed D50 |
|---|---:|
| Coarse | 100 µm |
| Medium | 30 µm |
| Fine | 10 µm |
| Micronised | 3 µm |

### 4.6 Pharmacokinetic Modelling

A simplified one-compartment pharmacokinetic model was implemented to investigate the downstream effects of dissolution on simulated plasma drug concentration.

The model incorporated:

- Drug absorption.
- Gastrointestinal transit.
- Drug elimination.
- Apparent volume of distribution.

The following parameters were calculated:

- Cmax: Maximum plasma concentration.
- Tmax: Time required to reach maximum plasma concentration.
- AUC0–12: Area under the plasma concentration-time curve over 12 hours.
- Fraction absorbed.
- Relative bioavailability compared with the simulated micronised formulation.

These outputs demonstrate how changes in dissolution behaviour can influence simulated pharmacokinetic profiles under the selected assumptions.

---

## 5. Data Analysis and Results

The simulations generated multiple datasets that were processed and compared to investigate the relationships between particle size, energy consumption, dissolution and pharmacokinetic behaviour.

### Key observations

**1. Particle Size Distribution**

The five size-reduction machines produced distinctly different particle size distributions.

The jet mill generated the finest simulated distribution, while the jaw crusher produced comparatively coarse particles.

The calculated specific surface area increased substantially with decreasing characteristic particle size.

**2. Energy Consumption and Efficiency**

Kick's, Rittinger's and Bond's models exhibited different energy-response characteristics across the investigated product-size range.

The comparison demonstrated the importance of considering both energy requirements and the amount of new surface generated during size reduction.

Under the selected assumptions, the ball mill showed the highest surface-energy efficiency among the five simulated machines.

**3. Sieve Analysis**

The simulated sieve analysis demonstrated the usefulness of sieve-based characterization for relatively coarse powders.

However, the jet-mill distribution fell largely below the finest sieve aperture, highlighting the limitations of sieve analysis for very fine powders and the potential need for alternative characterization methods such as laser diffraction.

**4. Dissolution Behaviour**

The simulated dissolution profiles indicated that finer particle distributions generally produced faster dissolution.

This behaviour was consistent with the increased surface area available for interaction with the dissolution medium.

**5. Pharmacokinetic Behaviour**

The simulated pharmacokinetic results showed increases in Cmax and AUC as particle size decreased across the investigated micronisation grades.

However, the improvement became progressively smaller at finer particle sizes, indicating diminishing returns under the selected model assumptions.

These observations should be interpreted as computational outcomes rather than experimentally established pharmaceutical performance.

---

## 6. Visualization and Computational Outputs

The Python notebook generates eight major visualization groups:

| Figure | Visualization |
|---|---|
| 1 | Particle size distribution curves for five machines |
| 2 | D10, D50, D90 and distribution span |
| 3 | Comparison of Kick's, Rittinger's and Bond's energy models |
| 4 | Crusher efficiency and new surface generation |
| 5 | Simulated sieve analysis and Rosin–Rammler fitting |
| 6 | Specific surface area versus particle size |
| 7 | Drug dissolution profiles |
| 8 | Simulated plasma concentration-time profiles |

The generated outputs are exported into a structured Excel workbook for further examination and comparison.

---

## 7. Tools and Technologies

| Technology | Application |
|---|---|
| Python | Computational simulation and mathematical modelling |
| NumPy | Numerical computations and array operations |
| Pandas | Data processing, tabulation and Excel export |
| Matplotlib | Scientific visualization |
| Jupyter Notebook | Interactive computational development |
| Microsoft Excel | Results organization and comparative data analysis |

---

## 8. Repository Structure

```text
particle-size-distribution-drug-bioavailability/
│
├── README.md
│
├── simulation/
│   └── PSD_Simulation_Notebook.ipynb
│
├── data/
│   └── PSD_Simulation_Results.xlsx
│
├── report/
│   └── Case_Study_Report.pdf
│
└── visualizations/
    ├── fig1_psd_curves.png
    ├── fig2_particle_size_metrics.png
    ├── fig3_energy_models.png
    ├── fig4_crusher_efficiency.png
    ├── fig5_sieve_analysis.png
    ├── fig6_surface_area.png
    ├── fig7_dissolution_profiles.png
    └── fig8_plasma_profiles.png
```

---

## 9. How to Run the Project

### Prerequisites

- Python 3.9 or later
- Jupyter Notebook or JupyterLab

### Install dependencies

```bash
pip install numpy pandas matplotlib openpyxl jupyter
```

### Run the simulation

1. Clone or download this repository.
2. Open the project directory.
3. Launch Jupyter Notebook.
4. Open `PSD_Simulation_Notebook.ipynb`.
5. Execute all cells sequentially.

The notebook generates the simulation tables, visualizations and Excel results workbook.

**Note:** The notebook uses a fixed random seed for reproducibility of the simulated sieve-measurement noise.

---

## 10. Assumptions and Limitations

This project is based on mathematical models and illustrative parameters.

The following limitations should be considered:

- All particle size distributions are simulated rather than experimentally measured.
- Particle properties, machine characteristics and actual energy consumption values are assumed.
- Particles are approximated as spherical for surface-area and dissolution calculations.
- The dissolution model uses simplified assumptions regarding diffusion, saturation and particle shrinkage.
- The pharmacokinetic model uses a simplified one-compartment representation.
- The model does not account for the complete physiological complexity of gastrointestinal drug absorption.
- Simulated bioavailability values should not be interpreted as clinical predictions.
- Sieve analysis has limited resolution for particle distributions below the finest sieve aperture.

The results are therefore intended for educational investigation, comparative modelling and understanding of underlying engineering and pharmaceutical principles.

---

## 11. Key Learnings and Skills Demonstrated

This project provided an opportunity to translate a defined scientific problem into a computational workflow.

**Problem Solving**
- Identifying the relationship between particle size distribution and drug dissolution.
- Breaking down a multidisciplinary problem into computationally manageable components.
- Selecting mathematical models to investigate specific engineering and pharmaceutical questions.

**Technical Development**
- Implementing mathematical models using Python.
- Developing computational simulations.
- Working with numerical arrays and structured datasets.
- Generating scientific visualizations.

**Data Analysis**
- Calculating particle size distribution descriptors.
- Comparing multiple engineering models.
- Evaluating simulated datasets.
- Interpreting trends across dissolution and pharmacokinetic profiles.

**Scientific Communication**
- Organizing computational outputs into structured Excel workbooks.
- Presenting results through visualizations and comparative tables.
- Documenting assumptions, methodology, limitations and conclusions.
- Connecting computational findings with pharmaceutical engineering concepts.

---

## 12. Conclusion

This project demonstrates how computational modelling can be used to investigate the interconnected roles of particle size distribution, size-reduction energy, dissolution kinetics and simulated drug bioavailability.

By integrating mathematical models, Python programming, numerical analysis and data visualization, the project establishes a computational framework for exploring pharmaceutical engineering concepts.

One of the central findings is that particle-size reduction can improve dissolution behaviour through increased specific surface area. However, the extent of improvement depends on the underlying assumptions and other formulation and manufacturing considerations.

The project also highlights the importance of distinguishing between theoretical models, simulated outcomes and experimentally validated results.

Ultimately, this work provided practical exposure to interdisciplinary problem-solving through computational tools and quantitative data analysis.

---

## 13. References

1. Amidon, G. L., Lennernäs, H., Shah, V. P., & Crison, J. R. (1995). A theoretical basis for a biopharmaceutic drug classification. *Pharmaceutical Research*, 12, 413–420. https://doi.org/10.1023/A:1016212804288

2. Butcher, J. C., Garg, S., Kim, D., & Sharma, P. (2008). A modified approach to predict dissolution and absorption of polydisperse powders. *Pharmaceutical Research*, 25, 2309–2311. https://doi.org/10.1007/s11095-008-9630-3

3. Khadka, P. et al. (2014). Pharmaceutical particle technologies: An approach to improve drug solubility, dissolution and bioavailability. *Asian Journal of Pharmaceutical Sciences*, 9(6), 304–316. https://doi.org/10.1016/j.ajps.2014.05.005

4. van der Zwaan, I., & Frenning, G. (2023). A new modelling approach for dissolution of polydisperse powders. *International Journal of Pharmaceutics*, 633, 122626. https://doi.org/10.1016/j.ijpharm.2023.122626

Additional regulatory and technical references are documented in the academic case study.

---

**Academic Project | Fluid Mechanics and Mechanical Operations (24BTEN2031)**

**Project Contributors:** Tamanna Hazra and Kritika Jain

**Institution:** GITAM (Deemed to be University)

