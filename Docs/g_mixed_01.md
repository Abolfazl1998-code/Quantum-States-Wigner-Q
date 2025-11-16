# Mixed State (|0⟩⟨0| + |1⟩⟨1|)/2

## Definition and Physical Significance

This mixed state represents a classical statistical mixture of vacuum and single-photon states with equal probabilities. Unlike quantum superpositions, this state lacks quantum coherence between the components, demonstrating the fundamental difference between classical mixtures and quantum superpositions.

### Mathematical Definition
```
ρ = (1/2)|0⟩⟨0| + (1/2)|1⟩⟨1|
```

**Key Difference from Superposition:** No off-diagonal terms (|0⟩⟨1| or |1⟩⟨0|)

## Theoretical Derivation

### Density Operator Properties
The density matrix is diagonal:
```
ρ = ½[1  0]
    [0  1]
```

This represents:
- **50% probability** of being in |0⟩ state
- **50% probability** of being in |1⟩ state  
- **No quantum coherence** between states

### Husimi-Q Function

For mixed states, the Q-function is the weighted average:
```
Q(α) = (1/π) ⟨α|ρ|α⟩ = (1/2)Q₀(α) + (1/2)Q₁(α)
```

Substituting known Q-functions:
```
Q₀(α) = (1/π) e^{-|α|²}
Q₁(α) = (1/π) |α|² e^{-|α|²}
```

Therefore:
```
Q(α) = (1/(2π)) [e^{-|α|²} + |α|² e^{-|α|²}]
```

```
Q(α) = (1/(2π)) (1 + |α|²) e^{-|α|²}
```

### Wigner Function

Similarly, for mixed states:
```
W(α) = (1/2)W₀(α) + (1/2)W₁(α)
```

Substituting known Wigner functions:
```
W₀(α) = (2/π) e^{-2|α|²}
W₁(α) = (2/π) (4|α|² - 1) e^{-2|α|²}
```

Combining:
```
W(α) = (1/2)(2/π) [e^{-2|α|²} + (4|α|² - 1) e^{-2|α|²}]
```

```
W(α) = (1/π) [1 + (4|α|² - 1)] e^{-2|α|²}
```

```
W(α) = (4/π) |α|² e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/(2π)) (1 + |α|²) e^{-|α|²}
```

### Wigner Function  
```
W(α) = (4/π) |α|² e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Rotationally symmetric** distribution
- **Always positive** Wigner function
- **No quantum interference** patterns
- **Classical-like behavior**

### Classical Mixture Properties
- **Statistical average** of component states
- **No coherence** between |0⟩ and |1⟩
- **Can be described** by classical probability theory
- **Zero quantum correlations**

### Field Properties
```
⟨â⟩ = 0
⟨â⁺â⟩ = 1/2
⟨(ΔX₁)²⟩ = 3/4
⟨(ΔX₂)²⟩ = 3/4
```

## Mathematica Implementation

### Code
```mathematica
(* Mixed State (|0⟩⟨0| + |1⟩⟨1|)/2: Wigner and Q Functions *)

(* Phase space coordinates *)
r2[x_, y_] := x^2 + y^2

(* Husimi-Q Function for Mixed State *)
QMixed01[x_, y_] := (1/(2*Pi)) * (1 + r2[x, y]) * Exp[-r2[x, y]]

(* Wigner Function for Mixed State *)
WMixed01[x_, y_] := (4/Pi) * r2[x, y] * Exp[-2*r2[x, y]]

(* 3D Plot of Q Function - Show rotational symmetry *)
Plot3D[QMixed01[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "Vista",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Q Function for Mixed State (|0⟩⟨0| + |1⟩⟨1|)/2",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 3D Plot of Wigner Function - Always positive *)
Plot3D[WMixed01[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "Rainbow", 
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for Mixed State (Always Positive/Classical)",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 2D Cross-section comparison *)
Plot[{WMixed01[x, 0], QMixed01[x, 0]}, {x, -3, 3},
 PlotLabel -> "Q and Wigner Functions (Cut at Im[α] = 0)",
 PlotLegends -> {"W(α) - Always Positive", "Q(α) - Always Positive"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}},
 PlotStyle -> {Directive[Thick, Blue], Directive[Dashed, Red]},
 Filling -> {1 -> Axis, 2 -> Axis},
 ImageSize -> Medium]

(* Comparison with superposition state *)
WSuperposition01[x_, y_] := (1/Pi) * (4*r2[x, y] + 4*x*(1 - 2*r2[x, y])) * Exp[-2*r2[x, y]]
Plot[{WMixed01[x, 0], WSuperposition01[x, 0]}, {x, -3, 3},
 PlotLabel -> "Comparison: Mixed vs Superposition State",
 PlotLegends -> {"Mixed State W(α)", "Superposition W(α)"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}},
 Filling -> {2 -> Axis}]
```

### Plot Analysis

#### Q Function Characteristics
- **Rotational symmetry**: Depends only on |α|²
- **Value at origin**: Q(0) = 1/(2π) ≈ 0.159
- **Maximum value**: ~0.117 at |α| = 1
- **Annular shape**: Similar to |1⟩ but with non-zero center
- **Always positive**: No negativity

#### Wigner Function Characteristics  
- **Rotational symmetry**: Perfect circular symmetry
- **Value at origin**: W(0) = 0
- **Maximum value**: ~0.47 at |α| = 0.5
- **Always positive**: No negative regions
- **Classical-like**: Can be described by classical probability

## Quantum-Classical Boundary Analysis

### Absence of Quantum Interference
- **No off-diagonal terms** in density matrix
- **No negative regions** in Wigner function
- **No asymmetry** in phase space
- **Statistical mixture** rather than quantum superposition

### Comparison with Superposition State

| Property | Mixed State | Superposition (|0⟩+|1⟩)/√2 |
|----------|-------------|---------------------|
| Wigner function | Always positive | Contains negative regions |
| Phase space symmetry | Rotational | Asymmetric |
| Quantum coherence | No coherence | Maximum coherence |
| ⟨â⟩ | 0 | 1/√2 |
| Classical description | Possible | Impossible |

## Experimental Significance

This state demonstrates:
- **Fundamental difference** between mixtures and superpositions
- **Classical limit** of quantum states
- **Decoherence effects** in quantum systems
- **Quantum-classical transition**

## Generation Methods

### Experimental Preparation
- **Statistical mixing** of prepared states
- **Decoherence processes**
- **Imperfect state preparation**
- **Thermal averaging**

### Distinguishing from Superpositions
- **Quantum state tomography**
- **Interference measurements**
- **Wigner function reconstruction**
- **Coherence witnesses**

## Special Notes

- Demonstrates **clear quantum-classical boundary**
- **Same diagonal elements** as superposition, different coherence
- **Wigner function positivity** indicates classical nature
- **Important benchmark** for quantum coherence studies

## Physical Realization

### Common Scenarios
- **Partially decohered** quantum states
- **Thermal states** at appropriate temperatures
- **Statistical ensembles** without phase relationships
- **Classical noise** added to quantum states

---

**Next State:** [Mixed State (|0⟩⟨0| + |4⟩⟨4|)/2](i_mixed_04.md)  
**Previous State:** [(|0⟩ + |4⟩)/√2 Superposition](g_superposition_0plus4.md)  
**Back to:** [Documentation Home](../README.md)
```
