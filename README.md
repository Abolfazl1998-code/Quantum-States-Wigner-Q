# Quantum States in Phase Space: Wigner and Husimi-Q Distributions

This repository provides theoretical derivations, Mathematica implementations, and graphical visualizations of Wigner and Husimi-Q quasi-probability distributions for nine fundamental quantum optical states. The project highlights **classical vs. nonclassical behavior**, **Wigner negativity**, **interference structure**, and **symmetry patterns** in phase space.

The analysis includes vacuum, coherent, Fock, superposition, and mixed states.

All states are accompanied by:
- Full theoretical derivations
- Mathematica implementation
- 3D Wigner and Q plots
- 2D cross-sections
- Interpretation of classical vs. nonclassical features

# States Included (a–i)

Full derivations for each state are available in the docs folder.

| ID | State | Category | Notes |
|----|-------|----------|-------|
| **a** | `|0>` | Classical-like | Gaussian, positive W |
| **b** | `|α0>` | Classical-like | Displaced Gaussian |
| **c** | `|1>` | Nonclassical | Negative W at center |
| **d** | `|4>` | Strongly nonclassical | Oscillations + multiple negative regions |
| **e** | `(|0> + |1>)/√2` | Nonclassical | Interference fringes (Re axis) |
| **f** | `(|0> + i|1>)/√2` | Nonclassical | Interference shifted to Im axis |
| **g** | `(|0> + |4>)/√2` | Highly nonclassical | 4-fold rotational interference |
| **h** | `(|0><0| + |1><1|)/2` | Classical-like | No negativities (no coherence) |
| **i** | `(|0><0| + |4><4|)/2` | Mixed-nonclassical | Symmetric but still negative W |

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

```
Quantum-States-Wigner-Q/
│
├── code/
│   ├── vacuum.nb
│   ├── coherent.nb
│   ├── fock1.nb
│   ├── fock4.nb
│   ├── superposition_01.nb
│   ├── superposition_0i1.nb
│   ├── superposition_04.nb
│   ├── mixed_01.nb
│   ├── mixed_04.nb
│
├── plots/
│   ├── vacuum_Q_3D.png
│   ├── vacuum_W_3D.png
│   ├── ...
│
├── docs/
│   ├── a_vacuum.md
│   ├── b_coherent.md
│   ├── c_fock1.md
│   ├── d_fock4.md
│   ├── e_superposition01.md
│   ├── f_superposition0i1.md
│   ├── g_superposition04.md
│   ├── h_mixed01.md
│   ├── i_mixed04.md
│
└── README.md
```

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

### Vacuum — Wigner
![vacuum](plots/vacuum_W_3D.png)

### Single Photon — Negative Wigner
![fock1](plots/fock1_W_3D.png)

### Coherent — Q Function
![coherent](plots/coherent_Q_3D.png)

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
