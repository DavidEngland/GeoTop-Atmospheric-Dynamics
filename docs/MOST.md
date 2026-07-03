# Geometric Interpretation of MOST

Monin-Obukhov Similarity Theory (MOST) can be taught as a geometric object: a smooth sub-manifold of quasi-equilibrium surface-layer states. This reframes MOST from a list of empirical fits into a structured closure geometry embedded in boundary-layer state space.

## 1. Invariant Scaling and What It Can (and Cannot) Determine

MOST uses the stability coordinate

$$
\zeta = \frac{z}{L},
$$

where $L$ is the Obukhov length.

For momentum, the standard definition is

$$
\phi_m(\zeta)=\frac{\kappa z}{u_*}\frac{\partial \bar u}{\partial z},
$$

with $\kappa$ the von Karman constant (typically about $0.40$).

In neutral conditions, convention is

$$
\phi_m(0)=1,
$$

so

$$
\frac{\partial \bar u}{\partial z}=\frac{u_*}{\kappa z}
\quad\Rightarrow\quad
\bar u(z)=\frac{u_*}{\kappa}\ln\!\left(\frac{z}{z_0}\right)
$$

(up to displacement-height and additive-constant conventions).

This is the precise complete-self-similarity statement (Barenblatt Type I): near $\zeta\to 0$, invariance fixes the neutral form.

Away from neutral, MOST functions are incomplete similarity (Type II): group invariance alone does not determine the full shape of $\phi_m(\zeta),\phi_h(\zeta)$. Additional closure assumptions are required.

## 2. Similarity Manifold and Parameter Roles

MOST defines a smooth similarity manifold in the larger boundary-layer state space.

- Fast variables (turbulent moments/fluxes) relax rapidly toward this manifold under scale separation.
- Slow external forcings (for example geostrophic wind tendency, net radiative cooling, surface thermal forcing) move the system through parameter space.
- Richardson numbers are best treated as diagnostic coordinates on the manifold, not as independent external controls.

This distinction prevents a common category error: using $Ri$ as if it were an exogenous bifurcation knob rather than a mixed diagnostic of forcing and response.

## 3. Folded Geometry: Static Shape vs Dynamic Trajectory

MOST closures can generate nonlinear flux-stability relations with folded equilibrium geometry.

- Static closure result: the manifold shape can include branches and folds.
- Dynamic trajectory claim ("ride branch -> hit fold -> jump") requires explicit time dynamics with a slow-fast split.

So the closure alone gives the geometric scaffold; a prognostic model is needed to define actual transitions and jump dynamics.

Post-fold interpretation should remain explicit as an open model question: whether VSBL is another branch of the same folded equilibrium family, or an alternate intermittent/oscillatory regime beyond classical similarity closure.

## 4. $\zeta$ Inversion Conditioning: Correct Algebra and Implications

### 4.1 Symmetric linear stable form

For

$$
\phi_m=\phi_h=1+\beta\zeta,
$$

we have

$$
Ri_g=\zeta\frac{\phi_h}{\phi_m^2}=\frac{\zeta}{1+\beta\zeta}.
$$

Quotient rule gives

$$
\frac{dRi_g}{d\zeta}
=\frac{(1)(1+\beta\zeta)-\zeta\beta}{(1+\beta\zeta)^2}
=\frac{1}{(1+\beta\zeta)^2}.
$$

So the derivative expression above is correct for this simplified case.

Also,

$$
Ri_g\to\frac{1}{\beta},\qquad
\frac{dRi_g}{d\zeta}\to 0\quad (\zeta\to\infty),
$$

hence inversion becomes ill-conditioned near the asymptotic ceiling.

### 4.2 Asymmetric Businger-Dyer variant

Using a common asymmetric stable pair,

$$
\phi_m=1+a\zeta,\qquad \phi_h=b+a\zeta,
$$

with typical values $a=4.7$, $b=0.74$,

$$
Ri_g=\zeta\frac{b+a\zeta}{(1+a\zeta)^2}.
$$

Then

$$
\frac{dRi_g}{d\zeta}
=\frac{b+a\zeta(2-b)}{(1+a\zeta)^3},
$$

which is positive for $a>0$, $b<2$ and tends to zero as $\zeta\to\infty$.

The asymptote is

$$
\lim_{\zeta\to\infty} Ri_g = \frac{1}{a}\approx 0.213\quad (a=4.7).
$$

So if a model computes $Ri_g$ above this ceiling while using this closure/inversion pair, no real $\zeta$ root exists in that branch.

### 4.3 Practical solver consequence

Near the asymptote, small changes in $Ri_g$ correspond to large changes in $\zeta$ (flat mapping). Newton-type inversion needs regime-aware initialization and safeguards (bounds, clipping, branch logic, or alternate stable closure forms) rather than a single unconstrained global solve.

## 5. Summary

| Traditional View | Geometric Interpretation |
| --- | --- |
| MOST scaling laws | Symmetry constraints near neutral plus closure-dependent incomplete similarity away from neutral |
| Empirical curves | A smooth similarity manifold in boundary-layer state space |
| Richardson number | Diagnostic coordinate, not generally an exogenous control parameter |
| Formula failure in strong stability | Near-boundary/near-asymptote geometric limitation requiring explicit dynamics and robust inversion logic |
