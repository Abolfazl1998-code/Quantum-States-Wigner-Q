# Quantum States in Phase Space: Wigner and Husimi-Q Distributions

![Mathematica](https://img.shields.io/badge/Mathematica-12.0+-DD1100)
![Quantum Optics](https://img.shields.io/badge/Field-Quantum%20Optics-0066CC)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Documentation](https://img.shields.io/badge/Docs-Comprehensive-blue)
![Research](https://img.shields.io/badge/Type-Research%20Project-purple)
![License](https://img.shields.io/badge/License-MIT-yellow)

This repository provides theoretical derivations, Mathematica implementations, and graphical visualizations of Wigner and Husimi-Q quasi-probability distributions for nine fundamental quantum optical states. The project highlights **classical vs. nonclassical behavior**, **Wigner negativity**, **interference structure**, and **symmetry patterns** in phase space.

The analysis includes vacuum, coherent, Fock, superposition, and mixed states.

All states are accompanied by:
- Full theoretical derivations
- Mathematica implementation
- 3D Wigner and Q plots
- 2D cross-sections
- Interpretation of classical vs. nonclassical features

## States Included (a-i)

Full derivations for each state are available in the docs folder.

| ID | State | Category | Notes |
|----|-------|----------|-------|
| a | Vacuum state | Classical-like | Gaussian, positive W |
| b | Coherent state | Classical-like | Displaced Gaussian |
| c | Single-photon state | Nonclassical | Negative W at center |
| d | Four-photon state | Strongly nonclassical | Oscillations + multiple negative regions |
| e | (0+1) superposition | Nonclassical | Interference fringes (Re axis) |
| f | (0+i1) superposition | Nonclassical | Interference shifted to Im axis |
| g | (0+4) superposition | Highly nonclassical | 4-fold rotational interference |
| h | Mixed state (0 & 1) | Classical-like | No negativities (no coherence) |
| i | Mixed state (0 & 4) | Mixed-nonclassical | Symmetric but still negative W |

## Project Goals

This project investigates:
- How different quantum states appear in phase space
- When and why **Wigner functions become negative**
- Effect of **coherence vs. incoherence** on quasi-probabilities
- Symmetry properties (rotational, axial, four-fold symmetry)
- Comparison between Gaussian classical states and strongly quantum states

Use cases:
- Quantum optics education
- Research visualization
- Studying nonclassicality
- Demonstrating quantum interference

## Method (Short Summary)

Phase-space variable:
```
α = x + i y, |α|² = x² + y²
```

### Q Function
```
Q(α) = (1/π) ⟨α|ρ|α⟩
```

### Wigner Function
For number states:
```
W(α) = (2/π) (-1)ⁿ Lₙ(4|α|²) e^(-2|α|²)
```

Extended to superpositions and mixtures via:
```
ρ = Σₙₘ ρₙₘ |n⟩⟨m|
```

Plots generated with **Plot3D**, **LaguerreL**, and custom Mathematica functions.

## Folder Structure


Quantum-States-Wigner-Q/
│
├── Mathematica-Code/
│   ├── vacuum_state.nb
│   ├── single_photon_n1.nb
│   ├── four_photon_n4.nb
│   ├── coherent_state_alpha3i.nb
│   ├── superposition_0plus1.nb
│   ├── superposition_0plusi1.nb
│   ├── mixed_01.nb
│   ├── mixed_alpha3.nb
│   └── cat_state_alpha3.nb
│
├── plots/
│   ├── vacuum_Wigner.png
│   ├── vacuum_Q.png
│   ├── vacuum_2D.png
│   ├── single_photon_n1_Wigner.png
│   ├── single_photon_n1_Q.png
│   ├── single_photon_n1_2D.png
│   ├── four_photon_n4_Wigner.png
│   ├── four_photon_n4_Q.png
│   ├── four_photon_n4_2D.png
│   ├── coherent_alpha3i_Wigner.png
│   ├── coherent_alpha3i_Q.png
│   ├── coherent_alpha3i_2D.png
│   ├── superposition_0plus1_Wigner.png
│   ├── superposition_0plus1_Q.png
│   ├── superposition_0plus1_2D.png
│   ├── superposition_0plusi1_Wigner.png
│   ├── superposition_0plusi1_Q.png
│   ├── superposition_0plusi1_2D.png
│   ├── mixed_01_Wigner.png
│   ├── mixed_01_Q.png
│   ├── mixed_01_2D.png
│   ├── mixed_alpha3_Wigner.png
│   ├── mixed_alpha3_Q.png
│   ├── mixed_alpha3_2D.png
│   ├── cat_state_alpha3_Wigner.png
│   ├── cat_state_alpha3_Q.png
│   └── cat_state_alpha3_2D.png
│
├── docs/
├── 01_theoretical_foundations.md
├── 02_mathematica_implementation.md 
├── a_vacuum_state.md
├── b_coherent_state.md
├── c_single_photon_state.md
├── d_four_photon_state.md
├── e_superposition_0plus1.md
├── f_superposition_0plusi1.md
├── g_mixed_01.md
├── h_mixed_04.md
└── i_schrodinger_cat.md
│
└── README.md

## Physical Summary of Results

### Classical-like states (always positive W)
- Vacuum
- Coherent
- Mixed (0/1)

Properties:
- Gaussian W
- No interference
- Minimum uncertainty

### Nonclassical states (negative W)
- Fock (`|1⟩`, `|4⟩`)
- Superpositions (`|0⟩ ± |1⟩`)
- Superposition (`|0⟩ + |4⟩`)
- Mixed (0/4)

Properties:
- Wigner negativity
- Interference fringes
- Oscillatory behavior
- Symmetry breaking depending on the state

### Symmetry Insights
- Fock + mixtures → rotational symmetry
- `(|0⟩ ± |1⟩)` → asymmetry along Re axis
- `(|0⟩ + i|1⟩)` → asymmetry along Im axis
- `(|0⟩ + |4⟩)` → four-fold rotational patterns

## Example Plots
(Full set in `/plots`)

### Vacuum State — Wigner Function
https://github.com/Abolfazl1998-code/Quantum-States-Wigner-Q/blob/main/Plots/vacuum_Wigner.png

### Single-Photon State — Negative Wigner
https://github.com/Abolfazl1998-code/Quantum-States-Wigner-Q/blob/main/Plots/single_photon_n1_Wigner.png

### Coherent State (α=3+i) — Q Function  
https://github.com/Abolfazl1998-code/Quantum-States-Wigner-Q/blob/main/Plots/coherent_alpha3i_Q.png

## How to Run
1. Open any `.nb` file in **code/**
2. Run all cells
3. Plots are generated and saved to **/plots** automatically

Requires **Mathematica 12+**

## References
- Christopher Gerry & Peter Knight — *Introductory Quantum Optics*
- U. Leonhardt — *Measuring the Quantum State of Light*
- M. Scully & M. Zubairy — *Quantum Optics*

## Author
**Abolfazl Amiri**  
MSc Physics (Condensed Matter) — MERC, Iran  
Email: [amiriabolfazl1998@gmail.com](mailto:amiriabolfazl1998@gmail.com)  
GitHub: [https://github.com/Abolfazl1998-code](https://github.com/Abolfazl1998-code)
