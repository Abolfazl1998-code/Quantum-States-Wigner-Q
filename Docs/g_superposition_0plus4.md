# Superposition State (|0⟩ + |4⟩)/√2

## Definition and Physical Significance

This superposition state represents a quantum coherent combination of vacuum and four-photon states. The large photon number difference (Δn=4) creates complex interference patterns with high-order rotational symmetry, demonstrating sophisticated quantum interference effects in phase space.

### Mathematical Definition
```
|ψ⟩ = (1/√2)(|0⟩ + |4⟩)
ρ = |ψ⟩⟨ψ| = (1/2)(|0⟩⟨0| + |4⟩⟨4| + |0⟩⟨4| + |4⟩⟨0|)
```

## Theoretical Derivation

### Density Operator Components
The density matrix contains:
- **Diagonal terms**: |0⟩⟨0| and |4⟩⟨4|
- **Off-diagonal terms**: |0⟩⟨4| and |4⟩⟨0| (high-order quantum coherence)

### Husimi-Q Function

Using the definition:
```
Q(α) = (1/π) ⟨α|ρ|α⟩
```

Substituting ρ:
```
Q(α) = (1/(2π)) [⟨α|0⟩⟨0|α⟩ + ⟨α|4⟩⟨4|α⟩ + ⟨α|0⟩⟨4|α⟩ + ⟨α|4⟩⟨0|α⟩]
```

Calculating each term:
```
⟨α|0⟩⟨0|α⟩ = e^{-|α|²}
⟨α|4⟩⟨4|α⟩ = (|α|⁸/24) e^{-|α|²}
⟨α|0⟩⟨4|α⟩ = (α⁴/√24) e^{-|α|²}
⟨α|4⟩⟨0|α⟩ = ((α*)⁴/√24) e^{-|α|²}
```

The coherence terms combine as:
```
⟨α|0⟩⟨4|α⟩ + ⟨α|4⟩⟨0|α⟩ = (1/√24)(α⁴ + (α*)⁴) e^{-|α|²}
```

Using α⁴ + (α*)⁴ = 2 Re[α⁴]:
```
= (2/√24) Re[α⁴] e^{-|α|²}
```

Therefore:
```
Q(α) = (1/(2π)) [1 + |α|⁸/24 + (2/√24) Re[α⁴]] e^{-|α|²}
```

### Wigner Function

Using the superposition principle:
```
W(α) = (1/2)[W₀(α) + W₄(α)] + W_interference(α)
```

The interference term for this high-order coherence is:
```
W_interference(α) = (2/π) (32/√24) Re[α⁴] e^{-2|α|²}
```

Combining all terms:
```
W(α) = (1/π) [1 + L₄(4|α|²) + (32/√24) Re[α⁴]] e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/(2π)) [1 + |α|⁸/24 + (2/√24) Re[α⁴]] e^{-|α|²}
```

### Wigner Function  
```
W(α) = (1/π) [1 + L₄(4|α|²) + (32/√24) Re[α⁴]] e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Four-fold rotational symmetry** in phase space
- **Complex interference** patterns
- **High-order quantum coherence**
- **Multiple negative regions**

### High-Order Coherence Effects
- **Re[α⁴] term** creates 4-fold symmetric interference
- **Large photon number difference** (Δn=4) enhances complexity
- **Multiple oscillation nodes** in phase space
- **Strong nonclassical character**

### Field Properties
```
⟨â⟩ = 0
⟨â⁴⟩ = √24/2 = 2√6 ≈ 4.90
⟨(ΔX₁)²⟩ = Complex pattern depending on orientation
```

## Mathematica Implementation

### Code
```mathematica
(* Superposition State (|0⟩ + |4⟩)/√2: Wigner and Q Functions *)

(* Phase space coordinates *)
r2[x_, y_] := x^2 + y^2
alpha4[x_, y_] := (x + I*y)^4  (* α⁴ for interference terms *)

(* Husimi-Q Function for (|0⟩ + |4⟩)/√2 *)
QSuperposition04[x_, y_] := (1/(2*Pi)) * 
  (1 + (r2[x, y]^4)/24 + (2/Sqrt[24])*Re[alpha4[x, y]]) * 
  Exp[-r2[x, y]]

(* Wigner Function for (|0⟩ + |4⟩)/√2 *)
WSuperposition04[x_, y_] := (1/Pi) * 
  (1 + LaguerreL[4, 4*r2[x, y]] + (32/Sqrt[24])*Re[alpha4[x, y]]) * 
  Exp[-2*r2[x, y]]

(* 3D Plot of Q Function - Show 4-fold symmetry *)
Plot3D[QSuperposition04[x, y], {x, -4, 4}, {y, -4, 4},
 PlotRange -> All,
 ColorFunction -> "BlueGreenYellow",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Q Function for (|0⟩ + |4⟩)/√2 Superposition",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 3D Plot of Wigner Function - Show complex interference *)
Plot3D[WSuperposition04[x, y], {x, -4, 4}, {y, -4, 4},
 PlotRange -> {-0.3, 0.8},
 ColorFunction -> "TemperatureMap",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for (|0⟩ + |4⟩)/√2 (High-Order Interference)",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 2D Cross-section along Re[α] axis *)
Plot[{WSuperposition04[x, 0], QSuperposition04[x, 0]}, {x, -4, 4},
 PlotLabel -> "Q and Wigner Functions (Cut at Im[α] = 0)",
 PlotLegends -> {"W(α) - Complex oscillations", "Q(α) - 4-fold structure"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}},
 PlotStyle -> {Directive[Thick, Blue], Directive[Dashed, Red]},
 Filling -> {1 -> Axis},
 ImageSize -> Medium]

(* Polar plot to demonstrate 4-fold symmetry *)
PolarPlot[QSuperposition04[r*Cos[θ], r*Sin[θ]] /. r -> 2, {θ, 0, 2*Pi},
 PlotLabel -> "Angular Dependence at |α|=2 (4-fold Symmetry)",
 AxesLabel -> {"Angle", "Q(α)"}]
```

### Plot Analysis

#### Q Function Characteristics
- **Four-fold symmetric pattern**: Re[α⁴] creates angular dependence
- **Maximum value**: Complex pattern with multiple peaks
- **Angular modulation**: Strong dependence on phase space angle
- **Always positive**: Maintains Q-function positivity
- **High-order structure**: More complex than lower superpositions

#### Wigner Function Characteristics  
- **Complex interference**: Multiple positive and negative regions
- **Four-fold symmetry**: Clear 4-fold rotational pattern
- **Multiple oscillation nodes**: Corresponding to n=4 coherence
- **Strong negativity**: Deep negative regions indicating high nonclassicality
- **Angular dependence**: Interference varies with phase space angle

## Quantum Interference Analysis

### High-Order Coherence
The |0⟩⟨4| and |4⟩⟨0| terms:
- **Create 4-fold symmetric** interference patterns
- **Generate multiple nodes** in phase space
- **Enhance nonclassical character** beyond simple superpositions
- **Demonstrate high-order** quantum effects

### Rotational Symmetry
- **Re[α⁴] = |α|⁴ cos(4θ)** creates 4-fold pattern
- **Angular period** of π/2 (90°)
- **Same structure** every 90° rotation
- **Higher complexity** than 2-fold patterns

## Comparison with Related States

### vs. (|0⟩ + |1⟩)/√2
| Property | (|0⟩+|4⟩)/√2 | (|0⟩+|1⟩)/√2 |
|----------|-------------|-------------|
| Symmetry | 4-fold rotational | 2-fold (directional) |
| Complexity | High | Moderate |
| Coherence order | 4th order | 1st order |
| Negative regions | Multiple, complex | Simple pattern |

### vs. Pure |4⟩ State
- **Additional interference** from vacuum component
- **Enhanced structure** due to coherence
- **Different symmetry** properties
- **Stronger nonclassical features**

## Experimental Significance

This state demonstrates:
- **High-order quantum coherence**
- **Complex interference patterns**
- **Quantum state engineering** capabilities
- **Fundamental limits** of quantum-classical correspondence

## Generation Methods

### Experimental Challenges
- **Maintaining coherence** between vastly different Fock states
- **Precise phase control** for high-order superpositions
- **Quantum state tomography** for verification
- **Stabilization** against decoherence

### Potential Techniques
- **Advanced quantum circuits**
- **Cavity QED** with precise timing
- **Optical frequency combs**
- **Quantum optimal control**

## Special Notes

- Demonstrates **quantum complexity** with simple components
- **High-order coherence** creates rich phase space structure
- **Symmetry properties** directly related to photon number difference
- **Experimental benchmark** for quantum state engineering

---

**Next State:** [Mixed State (|0⟩⟨0| + |1⟩⟨1|)/2](h_mixed_01.md)  
**Previous State:** [(|0⟩ + i|1⟩)/√2 Superposition](f_superposition_0plusi1.md)  
**Back to:** [Documentation Home](../README.md)
```
