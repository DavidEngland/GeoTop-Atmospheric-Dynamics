# Folded vs S-Shaped Manifolds in ABL Fast-Slow Models

This note clarifies an important distinction for stable boundary-layer (SBL) modeling:

- A **single fold** is not the same as a true **S-shaped manifold**.
- A true S-shape requires **two folds** and supports bistability/hysteresis.

## 1. Minimal Fast-Slow Toy Model

Let

- $x$: fast turbulence amplitude proxy (for example $x \propto \mathrm{TKE}^{1/2}$),
- $y$: slow stability/forcing proxy (for example inversion strength or cooling control).

Use

$$
\varepsilon \dot{x} = f(x,y) = Gx - Ax^2 - Byx - C, \qquad
\dot{y} = g(x,y), \qquad 0<\varepsilon\ll 1,
$$

with $A,B,C>0$.

The critical manifold is

$$
S_0 = \{(x,y): f(x,y)=0\}.
$$

Solving for $y$ (for $x>0$):

$$
y(x)=\frac{G}{B}-\frac{A}{B}x-\frac{C}{Bx}.
$$

## 2. What Geometry This Actually Gives

Differentiate:

$$
\frac{dy}{dx} = -\frac{A}{B} + \frac{C}{Bx^2}.
$$

Set to zero:

$$
x_f = \sqrt{\frac{C}{A}}.
$$

Second derivative:

$$
\frac{d^2y}{dx^2} = -\frac{2C}{Bx^3}<0 \quad (x>0),
$$

so $x_f$ is a strict local maximum.

**Conclusion:** this model has exactly **one fold**. It is a folded manifold, but not a full S-shaped manifold.

## 3. Normal Hyperbolicity at the Fold

For the fast subsystem,

$$
D_x f = \frac{\partial f}{\partial x} = G-2Ax-By.
$$

Substitute $By = G-Ax-C/x$ from the manifold equation:

$$
D_x f = -Ax + \frac{C}{x}.
$$

At $x_f=\sqrt{C/A}$,

$$
D_x f(x_f)=0,
$$

so normal hyperbolicity is lost at the fold. This is the local point where Fenichel persistence fails and fast adjustment becomes dominant.

## 4. Why This Is Not Yet the Full SBL Hysteresis Picture

A one-fold model can represent rapid collapse, but it cannot represent a robust two-threshold collapse/recovery loop by itself.

A true S-shaped manifold requires two folds, i.e., two turning points where

$$
\frac{dy}{dx}=0
$$

has two distinct real solutions on the physically relevant branch.

That usually appears after adding stronger nonlinear closure structure (for example nonlinear stability functions, nonlinear eddy diffusivity, or higher-order TKE closure terms) so the equilibrium relation effectively becomes cubic-like in $x$.

## 5. Physical Interpretation for ABL Regimes

For teaching and reporting, use conservative branch language:

- **Upper attracting branch:** sustained turbulent equilibrium.
- **Middle repelling branch:** unstable transition branch.
- **Lower attracting branch (when present):** weak/intermittent turbulence, not strictly laminar in most observations.

This aligns better with observed VSBL intermittency, wave-turbulence interactions, and bursty regeneration.

## 6. Where This Fits in the Course

This topic fits naturally in **Unit 3 (Dynamics, Bifurcations, and GSPT)**.

### 6.1 Unified State-Space Visualization

When presenting this sequence, explicitly connect the two labs to a geometric slice of cusp-type behavior:

- **Lab A (single fold):** trajectories pass one cliff edge; after collapse, the toy closure lacks a robust lower recovered shelf.
- **Lab B (two-fold S-curve):** trajectories drop to a lower weak-turbulence branch and remain there until a distinct recovery fold is crossed.

This side-by-side framing prevents the common conceptual mistake of equating one local saddle-node with full hysteresis geometry.

Recommended sequencing:

1. **Lab A: Single-fold model (this note).**
   - Derive $S_0$.
   - Locate fold and show loss of normal hyperbolicity.
   - Simulate fast collapse near fold crossing.
2. **Lab B: Two-fold (S-shaped) extension.**
   - Add nonlinear closure terms.
   - Identify both folds.
   - Demonstrate collapse/recovery hysteresis thresholds.

Learning objective: students distinguish local saddle-node geometry from full cusp-like hysteresis structure and connect each to what observations can and cannot establish.

### 6.2 Analytical Template for Lab B (Two-Fold Extension)

To bridge from Lab A to a true S-shape, use a minimally richer fast equation.

Option A (normal-form style):

$$
\varepsilon\dot{x}=\sigma+\beta x-x^3.
$$

Option B (atmospheric-flavored suppression):

$$
\varepsilon\dot{x}=\frac{Gx}{1+\gamma y}-Ax^2-C.
$$

In Lab B, students should derive the critical manifold and solve

$$
\frac{dy}{dx}=0
$$

to identify two distinct turning points (collapse and recovery folds) in the bistable parameter window.

## 7. Practical Modeling Note

When inverting diagnostic stability mappings (for example $Ri \leftrightarrow \zeta$), conditioning worsens near asymptotic ceilings where derivatives flatten. This numerical issue often coincides with near-fold transition zones.

For numerical methods, this means Jacobians become small or poorly conditioned, so Newton-Raphson updates can overshoot, oscillate, or diverge.

Practical safeguards:

- regime-aware initialization,
- bounded/root-bracketed solves,
- step damping or trust-region updates,
- physically consistent clipping near closure limits.

Pedagogical connection: physical loss of normal hyperbolicity and numerical ill-conditioning appear together in operational closure inversions.

## 8. Summary Matrix for Assessment

| Mathematical Feature | Lab A: Single-Fold Toy Model | Lab B: S-Shaped Extension |
| :--- | :--- | :--- |
| Order in fast variable $x$ | Quadratic-like balance | Cubic-like (or higher) balance |
| Number of equilibria ($\dot{x}=0$) | One physically relevant branch per control state | Up to three real branches in bistable window |
| Turning points ($dy/dx=0$) | One fold (local maximum in this note) | Two folds (collapse and recovery) |
| Atmospheric signature | Rapid evening collapse | Diurnal hysteresis (collapse and delayed recovery) |
| GSPT classification | Folded critical manifold / local saddle-node geometry | Cusp-like unfolded geometry with bistability |
| Modeling implication | Captures transition onset only | Captures both transition and recovery thresholds |

---

## Quick Summary

- The toy model above rigorously proves **one fold**.
- One fold is enough for local fast-slow transition analysis.
- A genuine **S-shaped manifold** requires **two folds**.
- For curriculum use, present this as a two-step arc: fold first, S-shape second.
