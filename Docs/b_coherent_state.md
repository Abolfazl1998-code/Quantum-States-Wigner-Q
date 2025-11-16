# Coherent State |α₀⟩

## Definition and Physical Significance

Coherent states are the quantum states that most closely resemble classical electromagnetic waves. They are eigenstates of the annihilation operator and maintain minimum uncertainty while having non-zero field amplitude.

### Mathematical Definition
```
â|α₀⟩ = α₀|α₀⟩
|α₀⟩ = D(α₀)|0⟩
```
where D(α₀) is the displacement operator.

## Theoretical Derivation

### Density Operator
```
ρ = |α₀⟩⟨α₀|
```

### Husimi-Q Function

The Q-function for a coherent state is:
```
Q(α) = (1/π) ⟨α|α₀⟩⟨α₀|α⟩ = (1/π) |⟨α|α₀⟩|²
```

The overlap between two coherent states is:
```
|⟨α|α₀⟩|² = e^{-|α - α₀|²}
```

Therefore:
```
Q(α) = (1/π) e^{-|α - α₀|²}
```

### Wigner Function

For coherent states, the Wigner function is:
```
W(α) = (2/π) e^{-2|α - α₀|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/π) e^{-|α - α₀|²}
```

### Wigner Function  
```
W(α) = (2/π) e^{-2|α - α₀|²}
```

## Physical Interpretation

### Key Features
- **Gaussian distribution** centered at α₀
- **Always positive** (classical-like behavior)
- **Minimum uncertainty state**
- **Displaced vacuum state**

### Field Properties
```
⟨â⟩ = α₀
⟨(ΔX₁)²⟩ = 1/4
⟨(ΔX₂)²⟩ = 1/4
```

The state exhibits Poissonian photon statistics:
```
P(n) = e^{-|α₀|²} |α₀|^{2n}/n!
```

## Mathematica Implementation

### Code for α₀ = 3 + i
```mathematica
(* Coherent State: Wigner and Q Functions *)

(* Coherent state amplitude *)
α0 = 3 + I;
reα0 = Re[α0];
imα0 = Im[α0];

(* Distance from coherent state center *)
distance2[x_, y_] := (x - reα0)^2 + (y - imα0)^2

(* Husimi-Q Function for Coherent State *)
QCoherent[x_, y_] := (1/Pi) * Exp[-distance2[x, y]]

(* Wigner Function for Coherent State *)
WCoherent[x_, y_] := (2/Pi) * Exp[-2*distance2[x, y]]

(* 3D Plot of Q Function *)
Plot3D[QCoherent[x, y], {x, 0, 6}, {y, -2, 4},
 PlotRange -> All,
 ColorFunction -> "SolarColors",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Husimi-Q Function for Coherent State |α₀⟩ with α₀ = 3 + i",
 BoxRatios -> {1, 1, 0.5}]

(* 3D Plot of Wigner Function *)
Plot3D[WCoherent[x, y], {x, 0, 6}, {y, -2, 4},
 PlotRange -> All,
 ColorFunction -> "SolarColors", 
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for Coherent State |α₀⟩ with α₀ = 3 + i",
 BoxRatios -> {1, 1, 0.5}]

(* 2D Cross-section through center *)
Plot[{WCoherent[x, imα0], QCoherent[x, imα0]}, {x, 0, 6},
 PlotLabel -> "Q and Wigner Functions (Cut through α₀)",
 PlotLegends -> {"W(α)", "Q(α)"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {{reα0}, {}}]
```

### Plot Analysis

#### Q Function Characteristics
- Maximum value: `1/π ≈ 0.318` at α = α₀
- Gaussian width: σ = 1
- Always positive
- Centered at α₀ = 3 + i

#### Wigner Function Characteristics  
- Maximum value: `2/π ≈ 0.637` at α = α₀
- Gaussian width: σ = 1/√2
- Always positive
- Narrower than Q function

## Special Properties

### Classical-like Behavior
- Positive-definite Wigner function
- Well-defined amplitude and phase
- Poissonian photon statistics
- Minimum uncertainty product

### Displacement Property
```
|α₀⟩ = D(α₀)|0⟩
D(α₀) = e^{α₀â⁺ - α₀*â}
```

### Completeness Relation
```
(1/π) ∫ d²α |α⟩⟨α| = 1
```

## Experimental Significance

Coherent states are crucial for:
- Laser physics (ideal laser output)
- Optical communications
- Quantum state tomography
- Reference states in quantum optics experiments

## Comparison with Vacuum State

- Vacuum state: α₀ = 0
- Coherent state: displaced vacuum
- Same uncertainty properties
- Different mean photon number: ⟨n⟩ = |α₀|²

## Parameter Variation

The properties depend on α₀:
- **Amplitude**: |α₀| determines mean photon number
- **Phase**: arg(α₀) determines field phase
- For α₀ = 3 + i: ⟨n⟩ = |3 + i|² = 10

---

**Next State:** [Single-Photon State](c_single_photon_state.md)  
**Previous State:** [Vacuum State](a_vacuum_state.md)  
**Back to:** [Documentation Home](../README.md)
```
