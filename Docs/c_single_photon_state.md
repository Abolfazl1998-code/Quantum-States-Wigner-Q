# Single-Photon State |1⟩

## Definition and Physical Significance

The single-photon state |1⟩ represents a quantum state with exactly one photon. It is the simplest nonclassical state and exhibits strong quantum characteristics that cannot be described by classical physics.

### Mathematical Definition
```
|ψ⟩ = |1⟩
ρ = |1⟩⟨1|
⟨n⟩ = ⟨1|â⁺â|1⟩ = 1
```

## Theoretical Derivation

### Husimi-Q Function

The Q-function for Fock states is:
```
Qₙ(α) = (1/π) |⟨α|n⟩|² = (1/π) e^{-|α|²} |α|^{2n}/n!
```

For n=1:
```
Q(α) = (1/π) e^{-|α|²} |α|²
```

### Wigner Function

For Fock states, the Wigner function is:
```
Wₙ(α) = (2/π) (-1)ⁿ Lₙ(4|α|²) e^{-2|α|²}
```

For n=1, using Laguerre polynomial L₁(ζ) = 1 - ζ:
```
W(α) = (2/π) (-1)¹ (1 - 4|α|²) e^{-2|α|²}
```

Therefore:
```
W(α) = (2/π) (4|α|² - 1) e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/π) |α|² e^{-|α|²}
```

### Wigner Function  
```
W(α) = (2/π) (4|α|² - 1) e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Nonclassical behavior** (negative Wigner function regions)
- **Annular distribution** in phase space
- **Zero amplitude at origin**
- **Quantum interference effects**

### Nonclassical Properties
- **Negative Wigner function** at origin
- **Sub-Poissonian statistics**
- **Photon antibunching**
- **Cannot be described by classical probability theory**

### Field Properties
```
⟨â⟩ = 0
⟨(ΔX₁)²⟩ = 3/4
⟨(ΔX₂)²⟩ = 3/4
⟨(ΔX₁)²⟩⟨(ΔX₂)²⟩ = 9/16 > 1/16
```

## Mathematica Implementation

### Code
```mathematica
(* Single-Photon State: Wigner and Q Functions *)

(* Phase space coordinates *)
r2[x_, y_] := x^2 + y^2

(* Husimi-Q Function for Single-Photon State *)
QSinglePhoton[x_, y_] := (1/Pi) * r2[x, y] * Exp[-r2[x, y]]

(* Wigner Function for Single-Photon State *)
WSinglePhoton[x_, y_] := (2/Pi) * (4*r2[x, y] - 1) * Exp[-2*r2[x, y]]

(* 3D Plot of Q Function *)
Plot3D[QSinglePhoton[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "SunsetColors",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Husimi-Q Function for Single-Photon State |1⟩",
 BoxRatios -> {1, 1, 0.5}]

(* 3D Plot of Wigner Function - Highlight Negative Regions *)
Plot3D[WSinglePhoton[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> {-0.7, 0.7},
 ColorFunction -> "Rainbow",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for Single-Photon State |1⟩ (Nonclassical)",
 BoxRatios -> {1, 1, 0.5}]

(* 2D Cross-section showing negative region *)
Plot[{WSinglePhoton[x, 0], QSinglePhoton[x, 0]}, {x, -3, 3},
 PlotLabel -> "Q and Wigner Functions (Cut at Im[α] = 0)",
 PlotLegends -> {"W(α) - Shows negativity", "Q(α) - Always positive"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {{-0.5, 0.5}, {0}},
 PlotStyle -> {Directive[Thick, Blue], Directive[Dashed, Red]},
 Filling -> {1 -> Axis}]
```

### Plot Analysis

#### Q Function Characteristics
- **Value at origin**: Q(0) = 0
- **Maximum value**: ~0.117 at |α| = 1
- **Annular shape**: Zero at center, peak at ring
- **Always positive**: No negativity

#### Wigner Function Characteristics  
- **Value at origin**: W(0) = -2/π ≈ -0.637
- **Zero crossing**: |α| = 0.5
- **Negative region**: Central area (|α| < 0.5)
- **Positive ring**: Outer region (|α| > 0.5)

## Quantum Interference Analysis

### Negative Wigner Function
The negative region at the origin represents:
- **Quantum interference** in phase space
- **Nonclassical nature** of the state
- **Impossibility** of classical description

### Physical Meaning
- At α=0: Strong quantum interference destructive
- The state cannot be localized at phase space origin
- Represents purely quantum fluctuations

## Experimental Significance

Single-photon states are crucial for:
- **Quantum cryptography** (BB84 protocol)
- **Quantum computing** (qubit implementations)
- **Quantum metrology** (precision measurements)
- **Fundamental tests** of quantum mechanics

## Generation Methods

### Common Techniques
- **Parametric down-conversion**
- **Quantum dots**
- **Single atoms/molecules**
- **Attenuated laser pulses** (approximate)

## Comparison with Classical States

| Property | Coherent State | Single-Photon State |
|----------|----------------|---------------------|
| Wigner function | Always positive | Negative regions |
| Photon statistics | Poissonian | Sub-Poissonian |
| ⟨â⟩ | α₀ ≠ 0 | 0 |
| Classical analog | Yes | No |

## Special Notes

- The single-photon state is the **simplest nonclassical state**
- Demonstrates clear **quantum-classical boundary**
- Negative Wigner function is **experimentally measurable**
- Serves as building block for **quantum information processing**

---

**Next State:** [Four-Photon State](d_four_photon_state.md)  
**Previous State:** [Coherent State](b_coherent_state.md)  
**Back to:** [Documentation Home](../README.md)
```
