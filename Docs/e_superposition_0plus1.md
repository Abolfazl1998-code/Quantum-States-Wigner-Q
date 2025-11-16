# Superposition State (|0⟩ + |1⟩)/√2

## Definition and Physical Significance

This superposition state represents a quantum coherent combination of vacuum and single-photon states. It demonstrates fundamental quantum interference effects and serves as a prototype for understanding quantum coherence in phase space.

### Mathematical Definition
```
|ψ⟩ = (1/√2)(|0⟩ + |1⟩)
ρ = |ψ⟩⟨ψ| = (1/2)(|0⟩⟨0| + |1⟩⟨1| + |0⟩⟨1| + |1⟩⟨0|)
```

## Theoretical Derivation

### Density Operator Components
The density matrix contains:
- **Diagonal terms**: |0⟩⟨0| and |1⟩⟨1|
- **Off-diagonal terms**: |0⟩⟨1| and |1⟩⟨0| (quantum coherence)

### Husimi-Q Function

Using the definition:
```
Q(α) = (1/π) ⟨α|ρ|α⟩
```

Substituting ρ:
```
Q(α) = (1/(2π)) [⟨α|0⟩⟨0|α⟩ + ⟨α|1⟩⟨1|α⟩ + ⟨α|0⟩⟨1|α⟩ + ⟨α|1⟩⟨0|α⟩]
```

Calculating each term:
```
⟨α|0⟩⟨0|α⟩ = e^{-|α|²}
⟨α|1⟩⟨1|α⟩ = |α|² e^{-|α|²}  
⟨α|0⟩⟨1|α⟩ = α e^{-|α|²}
⟨α|1⟩⟨0|α⟩ = α* e^{-|α|²}
```

Combining and using α + α* = 2Re[α] = 2x:
```
Q(α) = (1/(2π)) [(1 + |α|²) + 2x] e^{-|α|²}
```

### Wigner Function

The Wigner function can be derived from the superposition principle:
```
W(α) = (1/2)[W₀(α) + W₁(α)] + W_interference(α)
```

Where the interference term for this superposition is:
```
W_interference(α) = (2/π) (2x)(1 - 2|α|²) e^{-2|α|²}
```

Combining all terms:
```
W(α) = (1/π) [4|α|² + 4x(1 - 2|α|²)] e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/(2π)) (1 + |α|² + 2x) e^{-|α|²}
```

### Wigner Function  
```
W(α) = (1/π) [4|α|² + 4x(1 - 2|α|²)] e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Asymmetric distribution** in phase space
- **Quantum interference** patterns
- **Negative Wigner function** regions
- **Displaced maximum** from origin

### Quantum Coherence Effects
- **Off-diagonal terms** create interference
- **Asymmetry along Re[α] axis** (x-direction)
- **Phase-dependent** structure
- **Nonclassical behavior** despite classical components

### Field Properties
```
⟨â⟩ = 1/√2
⟨(ΔX₁)²⟩ = 3/4 - 1/√2 ≈ 0.043
⟨(ΔX₂)²⟩ = 3/4
```

## Mathematica Implementation

### Code
```mathematica
(* Superposition State (|0⟩ + |1⟩)/√2: Wigner and Q Functions *)

(* Phase space coordinates *)
r2[x_, y_] := x^2 + y^2

(* Husimi-Q Function for (|0⟩ + |1⟩)/√2 *)
QSuperposition01[x_, y_] := (1/(2*Pi)) * (1 + r2[x, y] + 2*x) * Exp[-r2[x, y]]

(* Wigner Function for (|0⟩ + |1⟩)/√2 *)
WSuperposition01[x_, y_] := (1/Pi) * 
  (4*r2[x, y] + 4*x*(1 - 2*r2[x, y])) * 
  Exp[-2*r2[x, y]]

(* 3D Plot of Q Function - Show asymmetry *)
Plot3D[QSuperposition01[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "DarkRainbow",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Q Function for (|0⟩ + |1⟩)/√2 Superposition",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 3D Plot of Wigner Function - Show interference patterns *)
Plot3D[WSuperposition01[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "ThermometerColors",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for (|0⟩ + |1⟩)/√2 (Quantum Interference)",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 2D Cross-section along Re[α] axis *)
Plot[{WSuperposition01[x, 0], QSuperposition01[x, 0]}, {x, -3, 3},
 PlotLabel -> "Q and Wigner Functions (Cut at Im[α] = 0)",
 PlotLegends -> {"W(α) - Shows interference", "Q(α) - Asymmetric"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}},
 PlotStyle -> {Directive[Thick, Blue], Directive[Dashed, Red]},
 Filling -> {1 -> Axis},
 ImageSize -> Medium]

(* Compare with mixed state for contrast *)
WMixed01[x_, y_] := (4/Pi) * r2[x, y] * Exp[-2*r2[x, y]]
Plot[{WSuperposition01[x, 0], WMixed01[x, 0]}, {x, -3, 3},
 PlotLabel -> "Comparison: Superposition vs Mixed State",
 PlotLegends -> {"Superposition W(α)", "Mixed State W(α)"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}}]
```

### Plot Analysis

#### Q Function Characteristics
- **Asymmetric distribution**: Shifted toward positive Re[α]
- **Maximum value**: ~0.18 at x ≈ 0.7, y=0
- **Non-zero at origin**: Q(0) = 1/(2π) ≈ 0.159
- **Always positive**: Maintains Q-function positivity

#### Wigner Function Characteristics  
- **Asymmetric interference**: Negative regions predominantly on left side
- **Multiple sign changes**: Complex oscillation pattern
- **Displaced structure**: Maximum shifted from origin
- **Quantum interference**: Clear signature of coherence

## Quantum Interference Analysis

### Coherence Terms Impact
The off-diagonal elements |0⟩⟨1| and |1⟩⟨0|:
- **Create asymmetry** in phase space
- **Generate negative regions** in Wigner function
- **Enable quantum interference** between components
- **Distinguish from classical mixtures**

### Phase Space Localization
- The state is **partially localized** in phase space
- **Not centered** at origin due to coherence
- **Interference fringes** visible as oscillations
- **Non-Gaussian** distribution

## Comparison with Related States

### vs. Mixed State (|0⟩⟨0| + |1⟩⟨1|)/2
| Property | Superposition | Mixed State |
|----------|---------------|-------------|
| Wigner function | Asymmetric, negative | Symmetric, positive |
| Coherence | Quantum coherence | No coherence |
| ⟨â⟩ | 1/√2 ≠ 0 | 0 |
| Classical description | No | Yes |

### vs. Single Components
- More structured than pure |0⟩ or |1⟩
- Exhibits properties of both components
- Additional interference features

## Experimental Significance

This superposition state is crucial for:
- **Quantum coherence studies**
- **Quantum information processing** (qubit operations)
- **Quantum state tomography**
- **Fundamental tests** of quantum mechanics

## Generation Methods

### Experimental Techniques
- **Quantum state engineering**
- **Optical networks** with beam splitters
- **Atomic systems** with precise control
- **Circuit QED** implementations

## Special Notes

- Demonstrates **clear quantum-classical boundary**
- **Coherence terms** are responsible for nonclassical features
- **Asymmetry direction** depends on relative phase
- Serves as **prototype** for understanding quantum superpositions

---

**Next State:** [(|0⟩ + i|1⟩)/√2 Superposition](f_superposition_0plusi1.md)  
**Previous State:** [Four-Photon State](d_four_photon_state.md)  
**Back to:** [Documentation Home](../README.md)
```
