# Geometric & Topological Methods in Atmospheric Dynamics
### Reference Card — UAH Graduate Course

---

## I. Differential Geometry

| Object | Definition |
|---|---|
| Physical manifold $\mathcal{M}$ | Smooth spatial domain (e.g., sphere) |
| Tangent bundle $T\mathcal{M}$ | Holds velocity vector fields $u$ |
| Cotangent bundle $T^*\mathcal{M}$ | Dual bundle; contains 1-form covectors $v$ |
| $k$-form | Multilinear functional on $k$ vectors |

**Graded algebra of forms on $\Omega^k(\mathcal{M})$:**
- **0-form** — scalar field ($\zeta$, $p$, $\theta$)
- **1-form** $v$ — velocity / circulation d.o.f.
- **2-form** $h$ — density/depth flux d.o.f.

**Key operators:**

| Operator | Action | Key property |
|---|---|---|
| Exterior derivative $d$ | $\Omega^k \to \Omega^{k+1}$ | $d^2 = 0$ (nilpotent) |
| Wedge product $\wedge$ | $\Omega^p \times \Omega^q \to \Omega^{p+q}$ | $\alpha \wedge \beta = (-1)^{pq}\,\beta \wedge \alpha$ |
| Hodge star $\star$ | $\Omega^k \to \Omega^{n-k}$ | metric-dependent |
| Interior product $\iota_u$ | $\Omega^k \to \Omega^{k-1}$ | contraction with $u$ |
| Lie derivative $\mathcal{L}_u$ | $\Omega^k \to \Omega^k$ | measures flow transport |

**Cartan's magic formula:**
$$\mathcal{L}_u \alpha = d(\iota_u \alpha) + \iota_u(d\alpha)$$

**Stokes' theorem:**
$$\int_{\partial M} \omega = \int_M d\omega$$

---

## II. Geometric Fluid Dynamics (Incompressible Euler)

**Vector-invariant momentum:**
$$\partial_t v + \iota_u \omega + dB = 0, \qquad \omega = dv$$

**Bernoulli function:** $\displaystyle B = \tfrac{1}{2}|u|^2 + p + \Phi$

**Mass conservation:** $d(\star v) = 0$

**Vorticity transport:** $\partial_t \omega + \mathcal{L}_u \omega = 0$

**Conserved invariants:**

| Invariant | Expression | Mechanism |
|---|---|---|
| Energy | $E = \tfrac{1}{2}\int_\Omega v \wedge \star v$ | Lamb vector $\iota_u\omega$ does no work |
| Kelvin circulation | $\tfrac{d}{dt}\oint_{c(t)} v = 0$ | consequence of $d^2 = 0$ |
| Helicity (3D) | $H = \int_\Omega v \wedge dv$ | knottedness of vortex lines |
| Potential vorticity | $q = (\omega + f)/\rho$ | material conservation |
| Enstrophy (2D) | $Z = \tfrac{1}{2}\int \omega^2\,dA$ | 2D inverse cascade |

---

## III. Discrete Exterior Calculus (DEC)

**Philosophy:** separate topology (combinatorial) from metric (geometric).

| Element | Description |
|---|---|
| Primal complex | Delaunay triangles; carries $k$-cochains |
| Dual complex | Voronoi polygons; carries $(n{-}k)$-cochains |
| Coboundary operator $D$ | discrete $d$; $D^2 = 0$ exactly |
| Discrete Hodge star $M_k$ | diagonal mass matrix; sole source of error |
| Whitney forms | interpolation from cochains to smooth forms |

**Discrete energy identity:** $\langle v,\, I_v(\tilde{D}_1 v)\rangle_1 = 0$ — unconditional stability, no artificial dissipation.

**Applications:** MPAS, ICON, mimetic finite differences, compatible finite elements.

---

## IV. Dynamical Systems & Bifurcation Theory

**Notation guardrail:** $M_0$ and $M_\epsilon$ denote phase-space critical/slow manifolds, not the physical manifold $\mathcal{M}$.

**Local bifurcations:**

| Type | Normal form | Atmospheric example |
|---|---|---|
| Saddle-node | $\dot{x} = \mu - x^2$ | tipping point |
| Pitchfork | $\dot{x} = \mu x - x^3$ | symmetry breaking |
| Transcritical | $\dot{x} = \mu x - x^2$ | threshold crossing |
| Hopf | $\dot{r} = \mu r - r^3$ | onset of oscillation |

**Global bifurcations:** homoclinic, heteroclinic, period-doubling, torus, crisis.

**Catastrophe theory (Thom):**

| Catastrophe | Codimension | Atmospheric relevance |
|---|---|---|
| Fold | 1 | sudden onset |
| Cusp | 2 | hysteresis, BL regime transitions |
| Swallowtail | 3 | multi-parameter tipping |
| Butterfly | 4 | — |

---

## V. Lagrangian Coherent Structures (LCS)

**Space split:** LCS are material structures embedded in the physical manifold $\mathcal{M}$, while $M_0$ and $M_\epsilon$ are invariant manifolds in abstract state space.

**Flow map:** $F_{t_0}^{t}(x_0)$ — trajectory from $x_0$ at $t_0$ integrated to $t$.

**Cauchy–Green deformation tensor:**
$$C = (DF_{t_0}^t)^\top DF_{t_0}^t$$

**Finite-Time Lyapunov Exponent (FTLE):**
$$\sigma_{t_0}^t(x_0) = \frac{1}{|t - t_0|} \ln\sqrt{\lambda_{\max}(C)}$$

**LCS types:**

| Type | FTLE field | Geometry |
|---|---|---|
| Repelling | forward ridges | unstable manifolds |
| Attracting | backward ridges | stable manifolds |
| Elliptic | closed material lines | vortex cores |
| Parabolic | jet-type surfaces | shear barriers |

**Atmospheric applications:** atmospheric rivers, hurricane eyewalls, jet streams, polar vortex edge, smoke/aerosol transport.

---

## VI. Topological Data Analysis (TDA)

**Persistent homology pipeline:**
$$\text{Point cloud} \xrightarrow{\text{Vietoris-Rips}} \text{Filtration} \xrightarrow{H_k} \text{Barcodes / Diagrams}$$

| Object | Meaning |
|---|---|
| $\beta_0$ (Betti 0) | connected components |
| $\beta_1$ (Betti 1) | loops / vortex rings |
| $\beta_2$ (Betti 2) | enclosed voids |
| Persistence diagram | birth–death pairs in feature space |
| Barcode | lifetime of topological features |
| Mapper | compressed topological graph of data |

**Atmospheric applications:** convective organization, cloud morphology, turbulence intermittency, regime detection, radar reflectivity analysis.

---

## VII. Atmospheric Boundary Layer Geometry

| Concept | Geometric interpretation |
|---|---|
| Monin–Obukhov similarity | manifold of similarity solutions |
| Stability regimes | folded equilibrium surface |
| Cusp bifurcation | hysteresis in BL regime transitions |
| Richardson number $Ri$ | coordinate on stability manifold |
| Slow manifold | reduced dynamics near criticality |
| Wave–turbulence interaction | resonant tori in phase space |
| Geometry-aware closures | differential-geometric TKE models |

**Key dimensionless numbers:**
$$Ri = \frac{(g/\theta_v)\,\partial_z\theta_v}{(\partial_z u)^2 + (\partial_z v)^2}, \qquad
Ro = \frac{U}{fL}, \qquad
Fr = \frac{U}{NH}$$
