# Four-Photon State |4⟩

## Definition and Physical Significance

The four-photon state |4⟩ represents a quantum state with exactly four photons. It exhibits strong nonclassical behavior with complex interference patterns in phase space, demonstrating the highly quantum nature of Fock states with higher photon numbers.

### Mathematical Definition
```
|ψ⟩ = |4⟩
ρ = |4⟩⟨4|
⟨n⟩ = ⟨4|â⁺â|4⟩ = 4
```

## Theoretical Derivation

### Husimi-Q Function

The Q-function for Fock states is:
```
Qₙ(α) = (1/π) e^{-|α|²} |α|^{2n}/n!
```

For n=4:
```
Q(α) = (1/π) e^{-|α|²} |α|⁸/24
```

### Wigner Function

For Fock states, the Wigner function is:
```
Wₙ(α) = (2/π) (-1)ⁿ Lₙ(4|α|²) e^{-2|α|²}
```

For n=4, using the 4th order Laguerre polynomial:
```
L₄(ζ) = 1 - 4ζ + 3ζ² - (2/3)ζ³ + (1/24)ζ⁴
```

Substituting ζ = 4|α|²:
```
L₄(4|α|²) = 1 - 16|α|² + 48|α|⁴ - (128/3)|α|⁶ + (32/3)|α|⁸
```

Therefore:
```
W(α) = (2/π) [1 - 16|α|² + 48|α|⁴ - (128/3)|α|⁶ + (32/3)|α|⁸] e^{-2|α|²}
```

## Final Results

### Husimi-Q Function
```
Q(α) = (1/(24π)) |α|⁸ e^{-|α|²}
```

### Wigner Function  
```
W(α) = (2/π) [1 - 16|α|² + 48|α|⁴ - (128/3)|α|⁶ + (32/3)|α|⁸] e^{-2|α|²}
```

## Physical Interpretation

### Key Features
- **Strongly nonclassical** behavior
- **Multiple negative regions** in Wigner function
- **Complex annular structure**
- **Four-fold oscillation pattern**

### Nonclassical Properties
- **Multiple negative regions** in phase space
- **Highly oscillatory** Wigner function
- **Sub-Poissonian statistics**
- **Quantum interference** with multiple nodes

### Field Properties
```
⟨â⟩ = 0
⟨(ΔX₁)²⟩ = 4.25
⟨(ΔX₂)²⟩ = 4.25
⟨(ΔX₁)²⟩⟨(ΔX₂)²⟩ = 18.0625 > 1/16
```

## Mathematica Implementation

### Code
```mathematica
(* Four-Photon State: Wigner and Q Functions *)

(* Phase space coordinates *)
r2[x_, y_] := x^2 + y^2

(* Husimi-Q Function for Four-Photon State *)
QFourPhoton[x_, y_] := (1/(24*Pi)) * (r2[x, y]^4) * Exp[-r2[x, y]]

(* Wigner Function for Four-Photon State - Using LaguerreL *)
WFourPhoton[x_, y_] := (2/Pi) * LaguerreL[4, 4*r2[x, y]] * Exp[-2*r2[x, y]]

(* Alternative explicit form for verification *)
WFourPhotonExplicit[x_, y_] := (2/Pi) * 
  (1 - 16*r2[x, y] + 48*r2[x, y]^2 - (128/3)*r2[x, y]^3 + (32/3)*r2[x, y]^4) * 
  Exp[-2*r2[x, y]]

(* 3D Plot of Q Function *)
Plot3D[QFourPhoton[x, y], {x, -4, 4}, {y, -4, 4},
 PlotRange -> All,
 ColorFunction -> "CMYKColors",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "Q(α)"},
 PlotLabel -> "Husimi-Q Function for Four-Photon State |4⟩",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 3D Plot of Wigner Function - Show oscillations and negative regions *)
Plot3D[WFourPhoton[x, y], {x, -4, 4}, {y, -4, 4},
 PlotRange -> {-0.2, 0.7},
 ColorFunction -> "TemperatureMap",
 Mesh -> None,
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"},
 PlotLabel -> "Wigner Function for Four-Photon State |4⟩ (Multiple Negative Regions)",
 BoxRatios -> {1, 1, 0.5},
 ImageSize -> Large]

(* 2D Cross-section showing complex structure *)
Plot[{WFourPhoton[x, 0], QFourPhoton[x, 0]}, {x, -4, 4},
 PlotLabel -> "Q and Wigner Functions (Cut at Im[α] = 0)",
 PlotLegends -> {"W(α) - Multiple oscillations", "Q(α) - Single peak"},
 AxesLabel -> {"Re[α]", "Value"},
 GridLines -> {None, {0}},
 PlotStyle -> {Directive[Thick, Blue], Directive[Dashed, Red]},
 Filling -> {1 -> Axis},
 ImageSize -> Medium]
```

### Plot Analysis

#### Q Function Characteristics
- **Value at origin**: Q(0) = 0
- **Maximum value**: ~0.034 at |α| ≈ 2.83
- **Annular shape**: Much broader than |1⟩ state
- **Always positive**: No negativity
- **Peak position**: Moves outward with increasing n

#### Wigner Function Characteristics  
- **Value at origin**: W(0) = 2/π ≈ 0.637 (positive for even n)
- **Multiple zero crossings**: Complex oscillation pattern
- **Negative regions**: Several concentric rings
- **Positive peaks**: Alternating with negative regions
- **Four-fold pattern**: Corresponding to n=4

## Quantum Interference Analysis

### Multiple Negative Regions
The complex pattern represents:
- **Higher-order quantum interference**
- **Multiple nodes** in phase space wavefunction
- **Strong nonclassical character**
- **n-dependent oscillation structure**

### Even vs Odd Fock States
- **Even n** (0, 2, 4, ...): Positive at origin
- **Odd n** (1, 3, 5, ...): Negative at origin
- **Oscillation number**: Related to photon number n

## Experimental Significance

Four-photon states are important for:
- **Quantum information processing** (multi-photon gates)
- **Quantum metrology** (Heisenberg-limited measurements)
- **Fundamental tests** of quantum mechanics
- **Quantum state engineering**

## Comparison with Lower Fock States

| Property | |1⟩ | |2⟩ | |4⟩ |
|----------|---|----|----|
| W(0) | Negative | Positive | Positive |
| Negative regions | 1 ring | 2 rings | 4 rings |
| Peak position | |α|≈1.0 | |α|≈1.7 | |α|≈2.8 |
| Complexity | Simple | Moderate | Complex |

## Generation Methods

### Experimental Techniques
- **Parametric down-conversion** (heralded photons)
- **Quantum dots** (deterministic sources)
- **Cavity QED** (strong coupling regimes)
- **Photon subtraction/addition** from other states

## Special Notes

- The |4⟩ state demonstrates **increasing complexity** with photon number
- **Negative regions grow** in number and complexity with n
- Represents **highly nonclassical** behavior
- Important for understanding **quantum-classical transition**

---

**Next State:** [(|0⟩ + |1⟩)/√2 Superposition](e_superposition_0plus1.md)  
**Previous State:** [Single-Photon State](c_single_photon_state.md)  
**Back to:** [Documentation Home](../README.md)
```
