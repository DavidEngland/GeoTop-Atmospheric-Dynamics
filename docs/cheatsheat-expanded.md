# Geometric & Topological Methods in Atmospheric Dynamics

### Reference Card — UAH Graduate Course

---

## I. Differential Geometry

| Object | Definition |
| --- | --- |
| Physical manifold $\mathcal{M}$ | Smooth spatial domain (e.g., sphere) |
| Tangent bundle $T\mathcal{M}$ | Holds velocity vector fields $u$ |
| Cotangent bundle $T^*\mathcal{M}$ | Dual bundle to $T\mathcal{M}$; contains 1-form covectors $v$ |
| $k$-form | Smooth, totally antisymmetric multilinear functional on $k$ tangent vectors |

**Graded algebra of forms ($\Omega^k(\mathcal{M})$):**

* **0-form** — scalar field ($\zeta$, $p$, $\theta$)
* **1-form** $v$ — velocity / circulation degrees of freedom (d.o.f.)
* **2-form** $h$ — density/depth flux d.o.f.

**Key operators:**

| Operator | Action | Key property |
| --- | --- | --- |
| Exterior derivative $d$ | $\Omega^k(M) \to \Omega^{k+1}(M)$ | $d^2 = 0$ (nilpotent; boundaries have no boundary) |
| Wedge product $\wedge$ | $\Omega^p(M) \times \Omega^q(M) \to \Omega^{p+q}(M)$ | Graded commutative: $\alpha \wedge \beta = (-1)^{pq}\,\beta \wedge \alpha$ |
| Hodge star $\star$ | $\Omega^k(M) \to \Omega^{n-k}(M)$ | Isomorphism; explicitly metric-dependent |
| Interior product $\iota_u$ | $\Omega^k(M) \to \Omega^{k-1}(M)$ | Contraction/inner product with a vector field $u$ |
| Lie derivative $\mathcal{L}_u$ | $\Omega^k(M) \to \Omega^k(M)$ | Measures transport/deformation along the flow of $u$ |

**Cartan's magic formula:**


$$\mathcal{L}_u \alpha = d(\iota_u \alpha) + \iota_u(d\alpha)$$

**Stokes' theorem:**


$$\int_{\partial M} \omega = \int_M d\omega$$

---

## II. Geometric Fluid Dynamics (Incompressible Euler)

**Vector-invariant momentum equation (as a 1-form equation):**


$$\partial_t v + \iota_u \omega + dB = 0, \qquad \text{where } \omega = dv$$

**Bernoulli function:** $\displaystyle B = \tfrac{1}{2}\iota_u v + p + \Phi$ *(Note: $\tfrac{1}{2}|u|^2$ is coordinate-free written as $\tfrac{1}{2}\iota_u v$)*

**Mass conservation (Incompressibility):** $d(\star v) = 0$

**Vorticity transport equation:**

$$\partial_t \omega + \mathcal{L}_u \omega = 0 \quad \implies \quad \partial_t \omega + d(\iota_u \omega) = 0$$

**Conserved Invariants:**

| Invariant | Expression | Physical Mechanism |
| --- | --- | --- |
| **Energy** | $E = \tfrac{1}{2}\int_M v \wedge \star v$ | Lamb vector 1-form $\iota_u\omega$ satisfies $\iota_u(\iota_u \omega) = 0$ (does no work) |
| **Kelvin circulation** | $\tfrac{d}{dt}\oint_{c(t)} v = 0$ | Direct consequence of Stokes' theorem and $\mathcal{L}_u v = -dB$ |
| **Helicity (3D)** | $H = \int_M v \wedge dv$ | Topological measure of the knottedness/linking of vortex lines |
| **Potential Vorticity** | $q = \star(dv \wedge d\theta) / \rho$ | Materially conserved ($Dq/Dt = 0$) in stratified, adiabatic flows |
| **Enstrophy (2D)** | $Z = \tfrac{1}{2}\int_M \omega \wedge \star \omega$ | Conserved in 2D; drives the clean atmospheric inverse energy cascade |

---

## III. Discrete Exterior Calculus (DEC)

**Philosophy:** Separate purely combinatorial topology (incidence matrices) from geometric measurements (lengths, areas, volumes).

| Element | Description |
| --- | --- |
| Primal complex | Simplical complex (e.g., Delaunay triangulation); carries primal $k$-cochains |
| Dual complex | Circumcentric dual (e.g., Voronoi tessellation); carries dual $(n{-}k)$-cochains |
| Coboundary operator $D$ | Discrete analog of $d$; defined purely combinatorially via the incidence matrix ($D^2 = 0$ holds exactly) |
| Discrete Hodge star $M_k$ | Diagonal/geometric mass matrix mapping primal to dual cochains; **the sole source of numerical error** |
| Whitney forms | Map discrete cochains back to continuous differential forms via interpolation |

**Discrete energy identity:** $\langle v,\, \iota_u(\tilde{D} v)\rangle = 0$

> Preserving the skew-symmetry of the convective term at the discrete level guarantees **unconditional structural stability** and absolutely zero artificial numerical dissipation of vorticity.

**Atmospheric Applications:** MPAS (Model for Prediction Across Scales), ICON, mimetic finite differences, and compatible/geometric finite elements.

---

## IV. Dynamical Systems & Bifurcation Theory

**Notation guardrail:** $M_0$ and $M_\epsilon$ denote phase-space critical/slow manifolds, not the physical manifold $\mathcal{M}$.

**Local Bifurcations ($\dot{x} = f(x, \mu)$):**

| Type | Normal Form | Atmospheric Example |
| --- | --- | --- |
| **Saddle-node** | $\dot{x} = \mu - x^2$ | Classic climate tipping points / EBM fold catastrophes |
| **Pitchfork** | $\dot{x} = \mu x - x^3$ | Symmetry breaking (e.g., Hadley cell transition to asymmetric monsoons) |
| **Transcritical** | $\dot{x} = \mu x - x^2$ | Fundamental threshold crossing (e.g., transition to instability) |
| **Hopf** | $\dot{z} = (\mu + i\omega)z - z\lvert z\rvert^2$ | Onset of oscillatory behavior (e.g., atmospheric wave patterns) |

**Global Bifurcations:** Homoclinic/heteroclinic connections, period-doubling cascades to chaos, torus breakdown, and interior/boundary crises.


**Catastrophe Theory (Thom's Classification):**

| Catastrophe | Codimension | Control Variables | Atmospheric Relevance |
| --- | --- | --- | --- |
| **Fold** | 1 | 1 ($\mu$) | Abrupt ecosystem/climate state onset |
| **Cusp** | 2 | 2 ($\alpha, \beta$) | **Bistability & Hysteresis**; Stratospheric warmings, boundary-layer transitions |
| **Swallowtail** | 3 | 3 | Multi-parameter interactive tipping (Ocean-Atmosphere-Ice coupling) |
| **Butterfly** | 4 | 4 | Complex structural stability boundaries in highly non-linear regime models |

---

## V. Lagrangian Coherent Structures (LCS)

**Space split:** LCS are material structures embedded in the physical manifold $\mathcal{M}$, while $M_0$ and $M_\epsilon$ are invariant manifolds in abstract state space.

**Flow Map:** $F_{t_0}^{t}(x_0) = x(t; t_0, x_0)$ — maps initial fluid parcel positions to their positions at time $t$ by integrating $\dot{x} = u(x,t)$.

**Cauchy–Green Deformation Tensor:**


$$C = (DF_{t_0}^t)^\top DF_{t_0}^t$$

**Finite-Time Lyapunov Exponent (FTLE):**


$$\sigma_{t_0}^t(x_0) = \frac{1}{|t - t_0|} \ln\sqrt{\lambda_{\max}(C(x_0))}$$

**LCS Taxonomy:**

| Type | FTLE Field | Geometry & Definition |
| --- | --- | --- |
| **Repelling** | Forward-time ridges | Material lines that maximize normal stretching; local unstable manifolds |
| **Attracting** | Backward-time ridges | Material lines that maximize normal compression; local stable manifolds |
| **Elliptic** | Closed/nested loops | Metrically non-stretching material loops; act as coherent vortex cores |
| **Parabolic** | Trench lines / shearing | Generalized material shear lines; act as physical transport barriers |

**Atmospheric Applications:** Mapping core boundaries of atmospheric rivers, hurricane eyewall shear containment, jet stream filaments, defining the edge of the polar vortex, and predictive ash/aerosol transport modeling.

---

## VI. Topological Data Analysis (TDA)

**Persistent Homology Pipeline:**


$$\text{Point Cloud / Field Data} \xrightarrow{\text{Vietoris-Rips / Sublevel Filtration}} \text{Filtered Complex Series} \xrightarrow{H_k} \text{Persistence Barcodes / Diagrams}$$

| Object | Mathematical Meaning | Physical Fluid/Atmospheric Meaning |
| --- | --- | --- |
| $\beta_0$ (Betti 0) | Rank of 0th homology group | Number of isolated, connected structures (e.g., cloud patches) |
| $\beta_1$ (Betti 1) | Rank of 1st homology group | Number of 2D loops, independent fluid circuits, or vortex rings |
| $\beta_2$ (Betti 2) | Rank of 2nd homology group | Enclosed 3D spatial voids or bubbles |
| **Persistence Diagram** | Multi-set of points $(b, d) \in \mathbb{R}^2$ | Plot of birth ($b$) vs. death ($d$) times of geometric structures |
| **Barcode** | Collection of intervals $[b, d]$ | Visual representation of feature lifetime; long bars denote true physical signal |
| **Mapper** | Topological visual graph skeleton | Low-dimensional network graph showing qualitative state trajectories of high-dimensional datasets |

**Atmospheric Applications:** Quantifying cellular convective organization, tracking lifecycle and morphology of cloud clusters, analyzing spatial turbulence intermittency, structural regime tracking, and parsing multiscale radar reflectivity maps.

---

## VII. Atmospheric Boundary Layer Geometry

| Concept | Geometric / Dynamical Interpretation |
| --- | --- |
| **Monin–Obukhov Similarity** | Invariant coordinate scaling defining a smooth sub-manifold of universal similarity solutions |
| **Stability Regimes** | Represented cleanly as a folded equilibrium surface exhibiting distinct structural stability transitions |
| **Cusp Bifurcation** | Explains the physical **hysteresis** found when transitioning between the Stable Boundary Layer (SBL) and Very Stable Boundary Layer (VSBL) |
| **Richardson Number ($Ri$)** | Serves as a critical bifurcation parameter / control coordinate on the stability manifold |
| **Slow Manifold** | Attracting invariant manifold where fast gravity-wave dynamics relax, leaving slow, balanced boundary-layer interactions |
| **Geometry-Aware Closures** | Writing subgrid-scale Reynolds stress tensors as explicit geometric invariants mapping directly to the background metric curvature |

**Key Dimensionless Ratios:**


$$Ri = \frac{\frac{g}{\theta_v}\frac{\partial \theta_v}{\partial z}}{\left(\frac{\partial u}{\partial z}\right)^2 + \left(\frac{\partial v}{\partial z}\right)^2}, \qquad
Ro = \frac{U}{fL}, \qquad
Fr = \frac{U}{NH}$$

---

### Suggested Revision Notes for Class Delivery:

1. **The Vector-Invariant Note:** Ensure you emphasize to the engineers that $\iota_u \omega$ is the geometric equivalent of the classic advection cross-product $u \times (\nabla \times u)$. This realization is an absolute "lightbulb moment" for them.
2. **Hodge Star Caution:** Remind students that while $d$ is completely free of metric coordinates, the Hodge star $\star$ introduces the geometry of the physical space (whether they are calculating on a flat 2D grid or a rotating, oblate spheroid Earth).