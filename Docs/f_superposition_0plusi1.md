# Superposition State (|0⟩ + i|1⟩)/√2

## Definition and Physical Significance

This superposition state represents a quantum coherent combination of vacuum and single-photon states with a π/2 relative phase. The imaginary unit 'i' introduces a phase difference that rotates the interference pattern in phase space, demonstrating the crucial role of quantum phase in superposition states.

### Mathematical Definition
```
|ψ⟩ = (1/√2)(|0⟩ + i|1⟩)
ρ = |ψ⟩⟨ψ| = (1/2)(|0⟩⟨0| + |1⟩⟨1| + i|1⟩⟨0| - i|0⟩⟨1|)
```

## Theoretical Derivation

### Density Operator Components
The density matrix contains:
- **Diagonal terms**: |0⟩⟨0| and |1⟩⟨1|
- **Off-diagonal terms**: i|1⟩⟨0| and -i|0⟩⟨1| (complex quantum coherence)

### Husimi-Q Function

Using the definition:
```
Q(α) = (1/π) ⟨α|ρ|α⟩
```

Substituting ρ:
```
Q(α) = (1/(2π)) [⟨α|0⟩⟨0|α⟩ + ⟨α|1⟩⟨1|α⟩ + i⟨α|1⟩⟨0|α⟩ - i⟨α|0⟩⟨1|α⟩]
```

Calculating each term:
```
⟨α|0⟩⟨0|α⟩ = e^{-|α|²}
⟨α|1⟩⟨1|α⟩ = |α|² e^{-|α|²}  
⟨α|0⟩⟨1|α⟩ = α e^{-|α|²}
⟨α|1⟩⟨0|α⟩ = α* e^{-|α|²}
```

The coherence terms become:
```
i⟨α|1⟩⟨0|α⟩ - i⟨α|0⟩⟨1|α⟩ = i(α* - α) e^{-|α|²}
```

Using α* - α = -2i Im[α] = -2iy:
```
i(-2iy) e^{-|α|²} = 2y e^{-|α|²}
```

Therefore:
```
Q(α) = (1/(2π)) [(1 + |α|²) + 2y] e^{-|α|²}
```

### Wigner Function

The Wigner function follows the superposition principle:
```
W(α) = (1/2)[W₀(α) + W₁(α)] + W_interference(α)
```

For this specific phase, the interference term is:
```
W_interference(α) = (2/π) (2y)(1 - 2|α|²) e^{-2|α|²}
```

Combining all terms:
```
W(α) = (1/π) [4|α|² + 4y(1 - 2|α|²)] e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/(2π)) (1 + |α|² + 2y) e^{-|α|²}
```

### Wigner Function  
```
W(α) = (1/π) [4|α|² + 4y(1 - 2|α|²)] e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Asymmetric distribution** along Im[α] axis (y-direction)
- **Quantum interference** patterns rotated by 90°
- **Negative Wigner function** regions
- **Phase-dependent** structure

### Quantum Phase Effects
- **Relative phase i** rotates interference pattern
- **Asymmetry along Im[α] axis** instead of Re[α]
- **Same magnitude**, different orientation compared to (|0⟩+|1⟩)/√2
- **Demonstrates importance** of quantum phase

### Field Properties
```
⟨â⟩ = i/√2
⟨(ΔX₁)²⟩ = 3/4
⟨(ΔX₂)²⟩ = 3/4 - 1/√2 ≈ 0.043
```

## Mathematica Implementation

### Code
```mathematica
(* Superposition State (|0⟩ + i|1⟩)/√2: Wigner and Q Functions *)

(* Phase space coordinates *)
r2[x_, y_] := x^2 + y^2

(* Husimi-Q Function for (|0⟩ + i|1⟩)/√2 *)
QSuperposition0I1[x_, y_] := (1/(2*Pi)) * (1 + r2[x, y] + 2*y) * Exp[-r2[x, y]]

(* Wigner Function for (|0⟩ + i|1⟩)/√2 *)
WSuperposition0I1[x_, y_] := (1/Pi) * 
  (4*r2[x, y] + 4*y*(1 - 2*r2[x, y])) * 
  Exp[-2*r2[x, y]]

(* 3D Plot of Q Function - Show vertical asymmetry *)
Plot3D[QSuperposition0I1[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "SolarColors",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Q Function for (|0⟩ + i|1⟩)/√2 Superposition",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 3D Plot of Wigner Function - Show vertical interference *)
Plot3D[WSuperposition0I1[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "RustTones",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for (|0⟩ + i|1⟩)/√2 (Vertical Interference)",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 2D Cross-section along Im[α] axis *)
Plot[{WSuperposition0I1[0, y], QSuperposition0I1[0, y]}, {y, -3, 3},
 PlotLabel -> "Q and Wigner Functions (Cut at Re[α] = 0)",
 PlotLegends -> {"W(α) - Vertical interference", "Q(α) - Vertical asymmetry"},
 AxesLabel -> {"Im[α]", "Value"},
 GridLines -> {None, {0}},
 PlotStyle -> {Directive[Thick, Blue], Directive[Dashed, Red]},
 Filling -> {1 -> Axis},
 ImageSize -> Medium]

(* Comparison with (|0⟩+|1⟩)/√2 to show phase rotation *)
QSuperposition01[x_, y_] := (1/(2*Pi)) * (1 + r2[x, y] + 2*x) * Exp[-r2[x, y]]
WSuperposition01[x_, y_] := (1/Pi) * (4*r2[x, y] + 4*x*(1 - 2*r2[x, y])) * Exp[-2*r2[x, y]]

Plot[{WSuperposition0I1[0, y], WSuperposition01[x, 0]/.x->y}, {y, -3, 3},
 PlotLabel -> "Comparison: Phase Rotation Effect",
 PlotLegends -> {"(0+i1) W(α) cut", "(0+1) W(α) cut (rotated)"},
 AxesLabel -> {"Coordinate", "Value"}]
```

### Plot Analysis

#### Q Function Characteristics
- **Vertical asymmetry**: Shifted toward positive Im[α]
- **Maximum value**: ~0.18 at x=0, y ≈ 0.7
- **Non-zero at origin**: Q(0) = 1/(2π) ≈ 0.159
- **Always positive**: Maintains Q-function positivity
- **90° rotation** compared to (|0⟩+|1⟩)/√2

#### Wigner Function Characteristics  
- **Vertical interference**: Negative regions predominantly on bottom side
- **Multiple sign changes**: Complex oscillation pattern along y-axis
- **Displaced structure**: Maximum shifted along imaginary axis
- **Phase-rotated interference**: Clear signature of quantum phase

## Quantum Phase Analysis

### Relative Phase Impact
The imaginary unit i = e^{iπ/2}:
- **Rotates interference pattern** by 90° in phase space
- **Changes asymmetry direction** from real to imaginary axis
- **Preserves quantum coherence** magnitude
- **Demonstrates phase control** in quantum states

### Phase Space Symmetry
- **Broken rotational symmetry** due to coherence
- **Directional preference** based on relative phase
- **Same degree of nonclassicality** as (|0⟩+|1⟩)/√2
- **Different spatial distribution**

## Comparison with Related States

### vs. (|0⟩ + |1⟩)/√2
| Property | (|0⟩+i|1⟩)/√2 | (|0⟩+|1⟩)/√2 |
|----------|---------------|-------------|
| Asymmetry axis | Im[α] (vertical) | Re[α] (horizontal) |
| ⟨â⟩ | i/√2 | 1/√2 |
| Wigner pattern | Rotated 90° | Original orientation |
| Physical meaning | Different phase | Reference phase |

### Phase Continuum
For general phase: (|0⟩ + e^{iφ}|1⟩)/√2
- φ = 0: Asymmetry along +Re[α]
- φ = π/2: Asymmetry along +Im[α] (this state)
- φ = π: Asymmetry along -Re[α]
- φ = 3π/2: Asymmetry along -Im[α]

## Experimental Significance

This state demonstrates:
- **Quantum phase control** importance
- **Phase-dependent** interference patterns
- **Quantum coherence manipulation**
- **Foundation for quantum gates** in quantum computing

## Generation Methods

### Experimental Techniques
- **Phase shifters** in optical networks
- **Microwave phase control** in circuit QED
- **Atomic state manipulation** with precise timing
- **Quantum gates** with controlled-phase operations

## Special Notes

- Demonstrates **quantum phase as physical observable**
- **Same state preparation** different phase setting
- **Interference pattern rotation** directly visible in phase space
- **Fundamental for understanding** quantum coherence and phase

---

**Next State:** [(|0⟩ + |4⟩)/√2 Superposition](g_superposition_0plus4.md)  
**Previous State:** [(|0⟩ + |1⟩)/√2 Superposition](e_superposition_0plus1.md)  
**Back to:** [Documentation Home](../README.md)
```
