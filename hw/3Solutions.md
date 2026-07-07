# Unit 3 Solution Key (Concise)

This document provides concise instructor-facing guidance for Problems 6 to 8.

## Problem 6. SBL as a Fast-Slow System

### A. Critical manifold

Given

$$
\dot e = f(e,\theta,\varepsilon), \qquad
\dot\theta = \varepsilon g(e,\theta,\varepsilon),
$$

the singular limit $\varepsilon\to 0$ gives

$$
0=f(e,\theta,0).
$$

So the critical manifold is

$$
S_0=\{(e,\theta):f(e,\theta,0)=0\}.
$$

Physical meaning: quasi-equilibrium between turbulence production and dissipation at fixed slow forcing.

### B. Folded geometry

In the canonical folded case, $S_0$ has attracting and repelling segments separated by fold points where

$$
\partial_e f = 0.
$$

Fast transitions occur near fold crossing, representing abrupt SBL collapse.

### C. Hysteresis

Within a bistable parameter window, collapse and recovery thresholds differ, producing hysteresis. This explains why restoring turbulence requires stronger forcing than the collapse threshold.

---

## Problem 7. Latitude as a Bifurcation Parameter

- Midlatitudes: folded or bistable structure is common under diurnal/synoptic forcing.
- Deep tropics: flatter manifold and weaker fold behavior are typical.
- Polar regimes: trajectories near non-hyperbolic regions violate Fenichel assumptions locally.

Key point: at folds, normal hyperbolicity is lost because a fast-subsystem eigenvalue crosses zero.

---

## Problem 8. Matched Asymptotics

Given

$$
\varepsilon \frac{de}{dt}=-(e-\bar e_0)^2+(\theta_0-\beta t),
$$

### A. Outer solution

Set $\varepsilon=0$:

$$
(e_{\text{out}}-\bar e_0)^2=\theta_0-\beta t,
$$

hence on the attracting branch,

$$
e_{\text{out}}(t)=\bar e_0+\sqrt{\theta_0-\beta t}.
$$

### B. Inner solution

Use $\tau=t/\varepsilon$ and leading-order fast equation near $t=0$:

$$
\frac{de_{\text{in}}}{d\tau}=-(e_{\text{in}}-\bar e_0)^2+\theta_0.
$$

A standard closed form (for appropriate initial condition) is

$$
e_{\text{in}}(\tau)=\bar e_0+\sqrt{\theta_0}\tanh\big(\sqrt{\theta_0}\,\tau + C\big).
$$

### C. Matching and composite

Use

$$
\lim_{t\to0^+}e_{\text{out}}(t)=\lim_{\tau\to\infty}e_{\text{in}}(\tau)
$$

to determine overlap and construct

$$
e_{\text{comp}}=e_{\text{out}}+e_{\text{in}}-e_{\text{overlap}}.
$$

Instructor note: full-credit responses should demonstrate the matching logic clearly even if an equivalent closed form is used.
