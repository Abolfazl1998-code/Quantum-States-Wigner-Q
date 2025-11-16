# Mathematica Implementation Guide

## Overview

This guide explains the Mathematica code structure used for computing and visualizing Wigner and Husimi-Q functions for various quantum states.

## Code Structure Pattern

Each Mathematica notebook follows this consistent structure:

### 1. Function Definitions
```mathematica
(* Define phase space coordinates *)
r2[x_, y_] := x^2 + y^2

(* Define Wigner and Q functions for specific state *)
WignerFunction[x_, y_] := ... 
QFunction[x_, y_] := ...
```

### 2. 3D Surface Plots
```mathematica
Plot3D[WignerFunction[x, y], {x, -3, 3}, {y, -3, 3},
 PlotRange -> All,
 ColorFunction -> "TemperatureMap",
 AxesLabel -> {"Re[α]", "Im[α]", "W(α)"}]
```

### 3. 2D Cross-sections
```mathematica
Plot[{WignerFunction[x, 0], QFunction[x, 0]}, {x, -3, 3},
 PlotLegends -> {"W(α)", "Q(α)"}]
```

### 4. Physical Analysis
- Interpretation of results
- Classical vs nonclassical behavior analysis
- Special features discussion

## Key Mathematica Functions Used

### Core Mathematical Functions
- `LaguerreL[n, x]` - Laguerre polynomials for Wigner functions
- `Exp[x]` - Exponential terms
- `Re[z]`, `Im[z]` - Complex number handling
- `Sqrt[x]` - Square roots for normalization

### Plotting Functions
- `Plot3D[]` - 3D surface plots of phase space distributions
- `Plot[]` - 2D cross-sections for detailed analysis
- `ColorFunction` - Highlight positive/negative regions
- `PlotRange` - Control visualization ranges

### Utility Functions
- `Style[text, options]` - Formatting plot labels
- `PlotLegends` - Adding legends to plots
- `AxesLabel` - Labeling coordinate axes

## Plotting Best Practices

### For Wigner Functions
```mathematica
(* Highlight negative regions *)
ColorFunction -> "TemperatureMap"
PlotRange -> All  (* Show negative values *)
```

### For Q Functions
```mathematica
(* Always positive, use different colormap *)
ColorFunction -> "SolarColors"
PlotRange -> {0, Automatic}  (* Start from zero *)
```

### Optimal Plot Ranges
- **Vacuum/Coherent States**: `{x, -3, 3}, {y, -3, 3}`
- **Fock States (n≥1)**: `{x, -4, 4}, {y, -4, 4}`
- **Superposition States**: `{x, -3, 3}, {y, -3, 3}`

## Common Patterns by State Type

### Fock States |n⟩
```mathematica
WignerFunction[x_, y_] := (2/Pi) * (-1)^n * 
  LaguerreL[n, 4*r2[x, y]] * Exp[-2*r2[x, y]]

QFunction[x_, y_] := (1/Pi) * (r2[x, y]^n / n!) * Exp[-r2[x, y]]
```

### Coherent States |α₀⟩
```mathematica
(* Distance from coherent state center *)
distance2[x_, y_] := (x - Re[α₀])^2 + (y - Im[α₀])^2

WignerFunction[x_, y_] := (2/Pi) * Exp[-2*distance2[x, y]]
QFunction[x_, y_] := (1/Pi) * Exp[-distance2[x, y]]
```

### Superposition States
```mathematica
(* Include interference terms *)
WignerFunction[x_, y_] := (1/2) * (W₀[x,y] + W₁[x,y] + W_interference[x,y])
```

## Performance Tips

1. **Use exact fractions** instead of decimal numbers for better precision
2. **Precompute common expressions** like `r2[x_, y_]` for efficiency
3. **Choose appropriate PlotPoints** balance between quality and speed
4. **Use specific ColorFunction** to highlight physical features

## Error Handling

### Common Issues and Solutions
- **Slow rendering**: Reduce `PlotPoints` or use smaller ranges
- **Missing features**: Check `PlotRange -> All`
- **Wrong colors**: Adjust `ColorFunction` for value ranges
- **Complex number errors**: Ensure proper handling of `Re` and `Im`

## Example Template

```mathematica
(* === QUANTUM STATE ANALYSIS === *)

(* 1. Define coordinates *)
r2[x_, y_] := x^2 + y^2

(* 2. Define state-specific functions *)
WignerFunction[x_, y_] := ... 
QFunction[x_, y_] := ...

(* 3. Create 3D visualizations *)
Plot3D[WignerFunction[x, y], {x, -3, 3}, {y, -3, 3},
 PlotLabel -> "Wigner Function", ...]

(* 4. Create 2D cross-sections *)
Plot[{WignerFunction[x, 0], QFunction[x, 0]}, {x, -3, 3},
 PlotLegends -> {"W(α)", "Q(α)"}]

(* 5. Physical interpretation *)
Print["Analysis: This state shows..."]
```
