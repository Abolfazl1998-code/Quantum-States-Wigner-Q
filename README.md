# Quantum States — Wigner & Husimi Q Functions (Mathematica)

Mathematica notebooks and visualizations for Wigner and Husimi-Q quasiprobability distributions of several quantum states (vacuum, coherent, Fock, superpositions, mixed and cat states).
![Representative Wigner plot](Plots/cat_state/cat_state_alpha3_Wigner.png)

> Representative Wigner function (Schrödinger cat, α=3). See `Plots/` for full gallery.

## Contents

- [Project overview](#project-overview)
- [Repository structure](#repository-structure)
- [Requirements & How to run](#requirements--how-to-run)
- [Theory & Key formulas](#theory--key-formulas)
- [States included](#states-included)
- [Reproducibility (step-by-step)](#reproducibility-step-by-step)
- [Docs & Derivations](#docs--derivations)
- [Gallery](#gallery)
- [References](#references)
- [Author](#author)

## Project overview

This project computes and visualizes Wigner and Husimi-Q quasiprobability distributions for a set of canonical quantum states of a single bosonic mode.  
Goals:
- Implement analytical expressions for Wigner and Q functions in Mathematica.
- Produce high-quality 3D and 2D visualizations suitable for teaching and research.
- Provide reproducible notebooks and documented code for PhD application / research portfolio.

## Repository structure

Quantum-States-Wigner-Q/
├── Mathematica-Code/ # notebooks (.nb) for each state
├── Plots/ # exported PNG/PDF visualizations
├── Docs/ # detailed theoretical derivations and short report (PDF/MD)
├── README.md # this file
└── .gitignore


## Theory & Key formulas

Let α = x + i y denote the complex phase-space coordinate (coherent state label), with |α|^2 = x^2 + y^2.

**Husimi-Q function** (for density matrix ρ):
\[
Q(α)=\frac{1}{\pi}\langle α|\rho|α\rangle
\]

**Wigner function** (symmetric ordering):
\[
W(α)=\frac{2}{\pi}\operatorname{Tr}\left[\rho\, D(α)\, \Pi\, D^\dagger(α)\right]
\]
(implementation uses standard expressions in α-space; see notebooks for explicit formulas.)

Common special cases (used in notebooks):
- Vacuum: \(Q(\alpha)=\frac{1}{\pi}e^{-|\alpha|^2},\; W(\alpha)=\frac{2}{\pi}e^{-2|\alpha|^2}\).
- Coherent |α₀⟩: \(Q(\alpha)=\frac{1}{\pi}e^{-|\alpha-\alpha_0|^2},\; W(\alpha)=\frac{2}{\pi}e^{-2|\alpha-\alpha_0|^2}\).
- Fock |n⟩: \(W_n(\alpha)=\frac{2}{\pi}(-1)^n L_n(4|\alpha|^2)e^{-2|\alpha|^2}\) and \(Q_n(\alpha)=\frac{1}{\pi}\frac{|\alpha|^{2n}}{n!}e^{-|\alpha|^2}\).
- Superpositions/mixed: see individual notebooks for explicit expressions.

## States included

Each notebook in `Mathematica-Code/` corresponds to one state:

- `vacuum_state.nb` — Vacuum |0⟩ (analytic Q and Wigner).
- `coherent_state_alpha3i.nb` — Coherent state |α₀⟩ with α₀ = 3 + i.
- `single_photon_n1.nb` — Fock state |1⟩ (nonclassical negativity).
- `four_photon_n4.nb` — Fock state |4⟩ (Laguerre oscillations).
- `superposition_0plus1.nb` — (|0⟩ + |1⟩)/√2 (interference).
- `superposition_0plusi1.nb` — (|0⟩ + i|1⟩)/√2 (phase-shifted interference).
- `mixed_01.nb` — ρ = (|0⟩⟨0| + |1⟩⟨1|)/2 (classical-like).
- `cat_state_alpha3.nb` — Schrödinger cat |α⟩ − |−α⟩, α = 3 (interference fringes).
- `mixed_coherent_alpha3.nb` — mixture of |α⟩ and |−α⟩ (no interference).

## Reproducibility (step-by-step)

1. Clone or download this repository.
2. Open `Mathematica-Code/<notebook>.nb`.
3. Evaluate the initialization cell (defines the functions: `QFunction...`, `WignerFunction...`).
4. Set parameters if needed (e.g., α in coherent/cat notebooks).
5. Evaluate the plotting cells to display 3D Q, 3D Wigner and 2D slice.
6. To export: run the Export cell or manually run:
   ```wolfram
   Export["Plots/<folder>/<file>.png", plotExpression, ImageResolution -> 300]
7. For batch export using WolframScript, see Docs/batch_export_example.md.


## 10) Docs & Derivations

```markdown
## Docs & Derivations

Detailed derivations, integrals and intermediate algebra are available in `Docs/`:
- `Docs/Wigner_definition_and_integral.md` — derivation from operator definition.
- `Docs/Q_function_and_coherent_states.md` — Husimi Q derivations.
- `Docs/report.pdf` — brief project report (if available).

## Gallery (representative)

### Vacuum
![vacuum Q thumbnail](Plots/vacuum/vacuum_Q.png)

### Single photon (|1>)
![n1 Wigner thumbnail](Plots/single_photon/single_photon_n1_Wigner.png)

### Cat state (α=3)
![cat Wigner thumbnail](Plots/cat_state/cat_state_alpha3_Wigner.png)

> See the `Plots/` folder for full-resolution images.

## Observations & notes

- Vacuum and coherent states show Gaussian Q and Wigner distributions (classical-like).
- Fock states (n≥1) exhibit oscillatory Wigner functions with regions of negativity — direct signature of nonclassicality.
- Superposition pure states present interference fringes; mixed states (incoherent mixtures) do not.
- Cat state displays interference fringes between two coherent components; strength depends on |α|.

## References

- Christopher Gerry & Peter Knight, *Introductory Quantum Optics*.

## Author

Abolfazl Amiri  
MSc Physics (Condensed Matter) — MERC, Iran  
Email: amiriabolfazl1998@gmail.com  
GitHub: https://github.com/Abolfazl1998-code
