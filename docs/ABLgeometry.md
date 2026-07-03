# ABL Geometry Module (Rigorous Version)

The Atmospheric Boundary Layer (ABL) geometry module reframes boundary-layer behavior as a fast-slow dynamical system in state space, rather than as a disconnected set of empirical formulas.

## 1. Quasi-Equilibrium Manifold of Turbulent States

The critical-manifold interpretation is valid after reduction to a fast-slow system, for example

$$
\varepsilon \dot{x}=f(x,y,\mu), \qquad \dot{y}=g(x,y,\mu), \qquad 0<\varepsilon\ll 1,
$$

where:

- $x$: fast turbulent variables (for example TKE, dissipation, flux adjustment terms)
- $y$: slow environmental variables (for example radiative cooling tendency, geostrophic forcing, soil/skin thermal state)

The critical manifold is

$$
S_0=\{(x,y): f(x,y,\mu)=0\},
$$

representing quasi-equilibrium turbulent states for fixed slow forcing.

For curriculum clarity, "quasi-equilibrium manifold of turbulent states" is preferable to "stability surface," which is less standard in boundary-layer literature.

## 2. Fold Geometry and Loss of Normal Hyperbolicity

In many reduced closures, the equilibrium geometry is folded (often S-shaped). A fold is identified by loss of normal hyperbolicity, e.g. in scalar fast dynamics by

$$
\frac{\partial f}{\partial x}=0,
$$

or more generally by singularity of $D_x f$.

Key interpretation points:

- Upper attracting branch: sustained turbulent equilibrium (often weakly stable SBL)
- Lower attracting branch: weakly or intermittently turbulent equilibrium (not necessarily laminar)
- Near fold: Fenichel persistence fails locally; trajectories may undergo rapid fast adjustment while slow variables are approximately frozen

Thus "snap" dynamics are trajectory statements about the reduced fast-slow model, not properties of a static closure by itself.

## 3. Reconstructing Geometry from Observations

Students do not reconstruct the true manifold directly. They reconstruct an empirical approximation in an observed/proxy state space.

A precise statement is:

High-frequency observations are embedded into a reconstructed state space whose geometry approximates the underlying slow manifold.

This naturally motivates:

- delay-coordinate embedding
- manifold learning / nonlinear dimensional reduction
- projection-awareness (observations sample a projection of full state)

Typical observables include velocity variance (TKE proxy), stratification measures, flux estimates, and forcing proxies from CASES-99, SHEBA, and Cabauw.

## 4. Coordinates, Controls, and Hysteresis

Richardson number is useful as a diagnostic state coordinate, but it should not be treated as the sole exogenous control parameter.

External controls are quantities like geostrophic forcing and net radiative forcing that evolve on slower timescales.

Hysteresis statement (catastrophe-theory consistent):

The control parameter can reverse direction while the trajectory remains on the attracting lower branch until the recovery fold is reached.

## 5. Latitude as Organizing Parameter (Not Direct Bifurcation Knob)

Latitude is best described as a higher-level organizing parameter that modifies physical controls through

- Coriolis parameter $f=2\Omega\sin\phi$
- solar and seasonal radiative forcing
- surface energy balance (including snow/ice effects)
- stratification climatology

These changes alter reconstructed manifold geometry across regimes.

Interpretive guidance:

- Mid-latitudes: folds and hysteresis are often clear in evening-transition datasets.
- Polar regimes: persistent inversions increase frequency of near-nonhyperbolic behavior; blow-up methods are relevant because trajectories often approach such regions, not because Arctic cases are categorically different mathematics.
- Tropical regimes: generally less time near strongly stable folded equilibria and more time in continuously forced convective states, while still allowing rich mesoscale organization.

## Summary Table: Geometric Reconstruction

| Geometric Feature | Dynamical Interpretation | Observational Signature |
| :--- | :--- | :--- |
| Critical manifold $S_0$ | Quasi-equilibrium turbulent states | Reconstructed from reduced state-space embeddings |
| Attracting upper branch | Sustained turbulent boundary layer | Large velocity variance, active turbulent fluxes |
| Attracting lower branch | Weak or intermittent turbulence | Smaller variance, stronger stratification |
| Fold curve | Loss of normal hyperbolicity | Rapid turbulence collapse in evening transition |
| Fast fibers | Rapid adjustment dynamics | Abrupt drops in TKE and momentum flux |
| Hysteresis loop | Path dependence between collapse and recovery | Different collapse/recovery thresholds |
| Latitude-dependent geometry | Changes induced via Coriolis, radiation, and surface energy balance | Contrasting CASES-99, SHEBA, and Cabauw behavior |

---

This framework for the **Atmospheric Boundary Layer (ABL) Geometry Module** is exceptionally sharp. Treating boundary-layer transitions as a fast-slow dynamical system cleanly bridges the gap between classic boundary-layer meteorology and geometric singular perturbation theory (GSPT). It elegantly reframes empirical phenomena—like the evening transition or turbulent intermittency—as intrinsic topological features of a state-space manifold rather than arbitrary "switching" functions.

Here is a targeted synthesis to further refine the pedagogical clarity, mathematical rigor, and observational alignment of this module.

---

## 1. Mathematical Structure of the Fast-Slow Split

To make the module truly rigorous, the fast-slow system can be explicitly cast in both the **fast time scale** ($\tau = t/\varepsilon$) and the **slow time scale** ($t$).

### Fast Time Scale ($\tau$)

As $\varepsilon \to 0$, the system approaches the **layer problem**:

$$\frac{dx}{d\tau} = f(x, y, \mu), \qquad \frac{dy}{d\tau} = 0$$

Here, the slow environmental variables $y$ are completely frozen, acting as parameters. The dynamics consist entirely of fast fibers rushing toward the critical manifold $S_0$.

### Slow Time Scale ($t$)

Taking $\varepsilon \to 0$ in the original system yields the **reduced problem** (or differential-algebraic system):

$$0 = f(x, y, \mu), \qquad \frac{dy}{dt} = g(x, y, \mu)$$

The dynamics are constrained to move strictly along $S_0$.

### Normal Hyperbolicity & Fenichel Theory

A subset of the critical manifold $S_0$ is **normally hyperbolic** if all eigenvalues of the Jacobian matrix $D_x f(x, y, \mu)$ have non-zero real parts.

- **Fenichel's Theorem** guarantees that for a sufficiently small $\varepsilon > 0$, this manifold persists as a slow manifold $S_\varepsilon$, maintaining its stability characteristics.
- When $D_x f$ becomes singular ($\det(D_x f) = 0$), normal hyperbolicity is lost. This is precisely where Fenichel theory breaks down, yielding the **fold curves** where trajectories "snap" away from the manifold along fast fibers.

---

## 2. Refining Observational Spaces vs. Control Spaces

One of the most valuable aspects of your module is the warning against treating the **Richardson number ($Ri$)** as an exogenous control. Because $Ri$ depends on the local, dynamically evolving wind shear and temperature gradients, it is fundamentally an *internal state variable* (or diagnostic coordinate).

To ground this for students, it is helpful to explicitly separate the spaces:

- **State Space (Internal Variables $x, y$):** TKE, local stratification ($Ri$), sensible heat flux ($H$), friction velocity ($u_*$).
- **Control Space (Exogenous Parameters $\mu$):** Geostrophic wind speed ($G$), free-tropospheric lapse rate ($\gamma$), deep soil temperature ($T_{soil}$), or downwelling top-of-atmosphere/surface radiative forcing ($R_{net}$).

### The Hysteresis Mechanism

When external forcing drives the slow variables across a fold point, the system undergoes a **fold bifurcation** (or saddle-node bifurcation of the fast subsystem).

```
  Turbulent Flux (x)
         ^
         |      =============> Upper Branch (Active Turbulence)
         |     /             |
         |    /              | Collapse (Fast Fiber)
         |   /               v
         |  /  <-- Fold 2
         | /                 |
         |/                  |
         +-------------------|--------------------> External Forcing / Geostrophic Wind (y)
                             |   /
            Recovery (Fast)  |  /
                             v /
               Lower Branch === (Intermittent / Weakly Stable)

```

Because the upper and lower branches overlap over a range of control values, reversing the external forcing does not trigger an immediate return. The boundary layer remains trapped on the lower branch until the slow drift reaches the *recovery fold* (Fold 2), mapping a classic **cusp catastrophe** geometry.

---

## 3. Grounding in Field Campaign Observables

To guide students through empirical reconstruction, we can explicitly map the theoretical fast-slow coordinates to the high-frequency datasets mentioned:

- **CASES-99 (Kansas, USA - Mid-latitude):** Ideal for observing the **evening transition**. Students can look for the sudden collapse of TKE and vertical velocity variance ($\sigma_w^2$) while geostrophic forcing remains steady—a clean visualization of a trajectory falling off an upper fold.
- **SHEBA (Arctic Ocean - Polar):** Characterized by prolonged periods spent near the lower branch or near the fold curve itself. The system frequently displays "global bifurcations" or continuous regime-switching driven by the surface energy balance over ice, showcasing non-hyperbolic persistence.
- **Cabauw (Netherlands - Coastal/Mid-latitude):** Excellent for long-term statistics on how changing seasonal solar radiation alters the underlying topology of the reconstructed manifold.

---

## 4. Methodological Toolkit for Students

When students reconstruct these states, standard linear tools like EOF (PCA) analysis will obscure the underlying topology because folds are inherently nonlinear. You might consider explicitly embedding these data-driven methodologies into the module:

1. **Takens' Delay Embedding Theorem:** Used to reconstruct the state space from single-variable time series (e.g., using time-delayed values of a sonic anemometer's temperature signal to reconstruct a proxy for the multi-dimensional attractor).
2. **Manifold Learning:** Utilizing non-linear dimensionality reduction techniques like **Isomap** or **Diffusion Maps** to visually unveil the S-shape or folded topology from high-frequency flux data.
3. **Geometric Blow-up Techniques:** For advanced students, this mathematical tool can be introduced to analyze the non-hyperbolic regions near the folds, explaining why the system "slows down" just before it collapses (critical slowing down).

This framework transforms boundary-layer meteorology from a catalog of empirical stability regimes into a cohesive, geometric branch of applied dynamical systems.

Would you like to expand on the specific mathematical formulations of a classic reduced closure (like a simplified $E-\varepsilon$ or single-column model) to show exactly how the S-shaped fold emerges analytically?
