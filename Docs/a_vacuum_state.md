# Vacuum State |0⟩

## Definition and Physical Significance

The vacuum state |0⟩ is the ground state of the quantum harmonic oscillator, representing a mode of the electromagnetic field with zero photons. It serves as the fundamental reference state in quantum optics.

### Mathematical Definition
```
|ψ⟩ = |0⟩
ρ = |0⟩⟨0|
```

## Theoretical Derivation

### Husimi-Q Function

The Q-function is defined as:
```
Q(α) = (1/π) ⟨α|ρ|α⟩
```

For vacuum state:
```
Q(α) = (1/π) ⟨α|0⟩⟨0|α⟩ = (1/π) |⟨α|0⟩|²
```

Using the coherent state expansion:
```
⟨α|0⟩ = e^{-|α|²/2}
```

Therefore:
```
Q(α) = (1/π) e^{-|α|²}
```

### Wigner Function

For Fock states, the Wigner function is:
```
Wₙ(α) = (2/π) (-1)ⁿ Lₙ(4|α|²) e^{-2|α|²}
```

For n=0 (vacuum state):
```
L₀(4|α|²) = 1
(-1)⁰ = 1
```

Thus:
```
W(α) = (2/π) e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/π) e^{-|α|²}
```

### Wigner Function  
```
W(α) = (2/π) e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Gaussian distribution** centered at origin (α=0)
- **Always positive** (classical-like behavior)
- **Minimum uncertainty state**
- **Rotational symmetry** in phase space

### Uncertainty Properties
```
⟨(ΔX₁)²⟩ = 1/4
⟨(ΔX₂)²⟩ = 1/4
⟨(ΔX₁)²⟩⟨(ΔX₂)²⟩ = 1/16  (Heisenberg limit)
```

## Mathematica Implementation

### Code
```mathematica
(* Vacuum State: Wigner and Q Functions *)

(* Phase space coordinates: α = x + iy *)
r2[x_, y_] := x^2 + y^2

(* Husimi-Q Function for Vacuum State *)
QVacuum[x_, y_] := (1/Pi) * Exp[-r2[x, y]]

(* Wigner Function for Vacuum State *)
WVacuum[x_, y_] := (2/Pi) * Exp[-2*r2[x, y]]

(* 3D Plot of Q Function *)
Plot3D[QVacuum[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "BlueGreenYellow",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Husimi-Q Function for Vacuum State |0⟩",
 BoxRatios -> {1, 1, 0.5}]

(* 3D Plot of Wigner Function *)
Plot3D[WVacuum[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "BlueGreenYellow", 
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for Vacuum State |0⟩",
 BoxRatios -> {1, 1, 0.5}]

(* 2D Cross-section Comparison *)
Plot[{WVacuum[x, 0], QVacuum[x, 0]}, {x, -3, 3},
 PlotLabel -> "Q and Wigner Functions (Cut at Im[α] = 0)",
 PlotLegends -> {"W(α)", "Q(α)"},
 AxesLabel -> {"Re[α]", "Value"},
 Filling -> Axis]
```

### Plot Analysis

#### Q Function Characteristics
- Maximum value: `1/π ≈ 0.318` at α=0
- Gaussian width: σ = 1
- Always positive
- Broader distribution than Wigner function

#### Wigner Function Characteristics  
- Maximum value: `2/π ≈ 0.637` at α=0
- Gaussian width: σ = 1/√2
- Always positive
- Narrower distribution than Q function

## Comparison with Other States

### Classical-like Properties
- No negative regions in Wigner function
- Gaussian shape
- Can be described by classical probability theory

### Quantum Aspects
- Represents quantum fluctuations (zero-point energy)
- Serves as reference for squeezed states
- Fundamental for understanding coherent states

## Experimental Significance

The vacuum state is crucial for:
- Understanding spontaneous emission
- Quantum noise limits in measurements
- Reference for squeezed state generation
- Quantum information protocols

## Special Notes

- The vacuum state is the **only** pure state that is also classical
- Both Q and W functions are Gaussian but with different widths
- Serves as building block for more complex states via displacement operator

---

**Next State:** [Coherent State](b_coherent_state.md)  
**Previous:** [Mathematica Implementation Guide](02_mathematica_implementation.md)  
**Back to:** [Documentation Home](../README.md)
```
