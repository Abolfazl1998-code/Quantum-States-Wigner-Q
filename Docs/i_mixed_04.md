# Mixed State (|0⟩⟨0| + |4⟩⟨4|)/2

## Definition and Physical Significance

This mixed state represents a classical statistical mixture of vacuum and four-photon states with equal probabilities. Despite being a mixture, the strong nonclassical character of the |4⟩ component persists, creating an interesting case where a mixed state can still exhibit quantum features.

### Mathematical Definition
```
ρ = (1/2)|0⟩⟨0| + (1/2)|4⟩⟨4|
```

**Key Characteristic:** Diagonal density matrix with no quantum coherence between components.

## Theoretical Derivation

### Density Operator Properties
The density matrix contains only diagonal elements:
```
ρ = ½[1  0  0  0  0]
    [0  0  0  0  0]  
    [0  0  0  0  0]
    [0  0  0  0  0]
    [0  0  0  0  1]
```

This represents:
- **50% probability** of being in |0⟩ state
- **50% probability** of being in |4⟩ state
- **No quantum coherence** between the states

### Husimi-Q Function

For mixed states, the Q-function is the weighted average:
```
Q(α) = (1/π) ⟨α|ρ|α⟩ = (1/2)Q₀(α) + (1/2)Q₄(α)
```

Substituting known Q-functions:
```
Q₀(α) = (1/π) e^{-|α|²}
Q₄(α) = (1/(24π)) |α|⁸ e^{-|α|²}
```

Therefore:
```
Q(α) = (1/(2π)) [e^{-|α|²} + (|α|⁸/24) e^{-|α|²}]
```

```
Q(α) = (1/(2π)) (1 + |α|⁸/24) e^{-|α|²}
```

### Wigner Function

Similarly, for mixed states:
```
W(α) = (1/2)W₀(α) + (1/2)W₄(α)
```

Substituting known Wigner functions:
```
W₀(α) = (2/π) e^{-2|α|²}
W₄(α) = (2/π) L₄(4|α|²) e^{-2|α|²}
```

Combining:
```
W(α) = (1/2)(2/π) [e^{-2|α|²} + L₄(4|α|²) e^{-2|α|²}]
```

```
W(α) = (1/π) [1 + L₄(4|α|²)] e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/(2π)) (1 + |α|⁸/24) e^{-|α|²}
```

### Wigner Function  
```
W(α) = (1/π) [1 + L₄(4|α|²)] e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Rotationally symmetric** distribution
- **Complex oscillatory** Wigner function
- **Negative regions** despite being mixed state
- **Hybrid classical-quantum** character

### Mixed State with Quantum Features
- **Statistical mixture** (no coherence)
- **Persistent negativity** from |4⟩ component
- **Demonstrates** that mixtures can be nonclassical
- **Intermediate case** between classical and quantum

### Field Properties
```
⟨â⟩ = 0
⟨â⁺â⟩ = 2
⟨(ΔX₁)²⟩ = Complex pattern
⟨(ΔX₂)²⟩ = Complex pattern
```

## Mathematica Implementation

### Code
```mathematica
(* Mixed State (|0⟩⟨0| + |4⟩⟨4|)/2: Wigner and Q Functions *)

(* Phase space coordinates *)
r2[x_, y_] := x^2 + y^2

(* Husimi-Q Function for Mixed State *)
QMixed04[x_, y_] := (1/(2*Pi)) * (1 + (r2[x, y]^4)/24) * Exp[-r2[x, y]]

(* Wigner Function for Mixed State *)
WMixed04[x_, y_] := (1/Pi) * (1 + LaguerreL[4, 4*r2[x, y]]) * Exp[-2*r2[x, y]]

(* 3D Plot of Q Function - Show rotational symmetry *)
Plot3D[QMixed04[x, y], {x, -4, 4}, {y, -4, 4},
 PlotRange -> All,
 ColorFunction -> "GrayYellowTones",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Q Function for Mixed State (|0⟩⟨0| + |4⟩⟨4|)/2",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 3D Plot of Wigner Function - Show oscillations and negative regions *)
Plot3D[WMixed04[x, y], {x, -4, 4}, {y, -4, 4},
 PlotRange -> {-0.2, 0.7},
 ColorFunction -> "TemperatureMap",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for Mixed State (Negative Regions Present)",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 2D Cross-section showing oscillatory structure *)
Plot[{WMixed04[x, 0], QMixed04[x, 0]}, {x, -4, 4},
 PlotLabel -> "Q and Wigner Functions (Cut at Im[α] = 0)",
 PlotLegends -> {"W(α) - Oscillatory with negativity", "Q(α) - Smooth and positive"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}},
 PlotStyle -> {Directive[Thick, Blue], Directive[Dashed, Red]},
 Filling -> {1 -> Axis},
 ImageSize -> Medium]

(* Comparison with (|0⟩+|4⟩)/√2 superposition *)
WSuperposition04[x_, y_] := (1/Pi) * (1 + LaguerreL[4, 4*r2[x, y]] + (32/Sqrt[24])*Re[(x + I*y)^4]) * Exp[-2*r2[x, y]]
Plot[{WMixed04[x, 0], WSuperposition04[x, 0]}, {x, -4, 4},
 PlotLabel -> "Comparison: Mixed vs Superposition State",
 PlotLegends -> {"Mixed State W(α)", "Superposition W(α)"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}}]
```

### Plot Analysis

#### Q Function Characteristics
- **Rotational symmetry**: Perfect circular symmetry
- **Value at origin**: Q(0) = 1/(2π) ≈ 0.159
- **Maximum value**: ~0.017 at |α| ≈ 2.83
- **Broad annular shape**: Much broader than |1⟩ mixture
- **Always positive**: No negativity

#### Wigner Function Characteristics  
- **Rotational symmetry**: Perfect circular symmetry
- **Value at origin**: W(0) = 2/π ≈ 0.637 (positive)
- **Complex oscillations**: Multiple positive and negative regions
- **Negative regions**: Present despite being mixed state
- **Hybrid character**: Mixed state with quantum features

## Quantum-Classical Analysis

### Persistence of Quantum Features
- **Negative Wigner regions** from |4⟩ component
- **Oscillatory structure** survives statistical mixing
- **Demonstrates** that nonclassicality ≠ coherence
- **Mixed states can be nonclassical**

### Comparison with Other Mixed States

| Property | Mixed (0+1) | Mixed (0+4) |
|----------|-------------|-------------|
| Wigner function | Always positive | Contains negative regions |
| Classical description | Possible | Impossible |
| Source of nonclassicality | None | |4⟩ component |
| Complexity | Simple | Complex oscillatory |

## Experimental Significance

This state demonstrates:
- **Nonclassical mixed states** existence
- **Decoherence doesn't always** destroy quantum features
- **Importance of component states** in mixtures
- **Quantum-classical transition** complexity

## Generation Methods

### Experimental Preparation
- **Statistical mixing** of prepared |0⟩ and |4⟩ states
- **Partial decoherence** of superposition states
- **Thermal averaging** at specific conditions
- **Imperfect quantum state preparation**

### Quantum State Engineering
- **Controlled decoherence** experiments
- **Quantum process tomography**
- **Wigner function reconstruction**
- **Nonclassicality measures**

## Special Notes

- Challenges the **simplistic view** that mixtures are always classical
- Demonstrates **component-dependent** quantum features
- **Wigner negativity persists** despite lack of coherence
- Important for understanding **decoherence processes**

## Physical Interpretation

### Statistical vs Quantum Properties
- **Statistical uncertainty**: Which state the system is in
- **Quantum uncertainty**: Inherent in each component state
- **The |4⟩ component** maintains its quantum character
- **The mixture** preserves this quantum character

### Implications for Quantum Foundations
- **Nonclassicality ≠ coherence**
- **Mixed states can exhibit** quantum features
- **Decoherence pathways** can be complex
- **Quantum-classical boundary** is nuanced

---

**Next State:** [Schrödinger Cat State](j_schrodinger_cat.md)  
**Previous State:** [Mixed State (|0⟩⟨0| + |1⟩⟨1|)/2](h_mixed_01.md)  
**Back to:** [Documentation Home](../README.md)
```
