# Theoretical Foundations: Wigner and Husimi-Q Functions

## Introduction to Phase Space Representations

In quantum optics, phase space representations provide a complete description of quantum states using quasi-probability distributions. Unlike classical systems where a state can be represented as a point in phase space, quantum states require distribution functions due to the uncertainty principle.

## Mathematical Definitions

### Phase Space Coordinates
We use complex variable notation:
```
α = x + iy = X₁ + iX₂
```
where:
- `x = Re[α]` (Real quadrature)
- `y = Im[α]` (Imaginary quadrature) 
- `X₁, X₂` are the quadrature operators

### Wigner Function
The Wigner function is defined as:
```
W(α) = (2/π) ∫ d²β ⟨-β|ρ|β⟩ e^{2(αβ* - α*β)}
```

#### For Fock States |n⟩:
```
Wₙ(α) = (2/π) (-1)ⁿ Lₙ(4|α|²) e^{-2|α|²}
```
where `Lₙ` is the nth Laguerre polynomial.

### Husimi-Q Function
The Q-function represents the overlap with coherent states:
```
Q(α) = (1/π) ⟨α|ρ|α⟩
```

#### For Fock States |n⟩:
```
Qₙ(α) = (1/π) (|α|²ⁿ/n!) e^{-|α|²}
```

## Key Physical Concepts

### Classical vs Nonclassical States

#### Classical-like States (Always Positive Wigner Function)
- Vacuum State |0⟩
- Coherent States |α⟩
- Mixed States without coherence

**Properties:**
- Gaussian distributions
- No negative regions in Wigner function
- Can be described by classical probability theory

#### Nonclassical States (Negative Wigner Regions)
- Fock States |n⟩ (n ≥ 1)
- Quantum Superpositions
- Schrödinger Cat States

**Properties:**
- Negative values in Wigner function
- Quantum interference patterns
- Cannot be described by classical probability theory

### Quantum Interference in Phase Space

Superposition states exhibit interference patterns visible as:
- Oscillations in phase space distributions
- Negative regions in Wigner functions
- Asymmetric distributions for specific superpositions

## Mathematical Properties

### Normalization
Both functions are normalized:
```
∫ W(α) d²α = 1
∫ Q(α) d²α = 1
```

### Marginal Distributions
The Wigner function gives correct marginal probability distributions:
```
∫ W(x,y) dx = P(y)
∫ W(x,y) dy = P(x)
```

### Uncertainty Principle
The functions respect the uncertainty principle:
```
⟨(ΔX₁)²⟩⟨(ΔX₂)²⟩ ≥ 1/16
```

## Computational Methods

### Analytical Approach
1. Define the density matrix ρ
2. Compute overlap integrals
3. Derive closed-form expressions

### Numerical Implementation
1. Discretize phase space
2. Compute function values on grid
3. Generate 2D and 3D visualizations

## References

1. Cahill & Glauber, "Ordered Expansions in Boson Amplitude Operators" (1969)
2. Leonhardt, "Measuring the Quantum State of Light" (1997)
3. Scully & Zubairy, "Quantum Optics" (1997)

**Next:** [Mathematica Implementation Guide](02_mathematica_implementation.md) | [Back to Documentation Home](../README.md)
