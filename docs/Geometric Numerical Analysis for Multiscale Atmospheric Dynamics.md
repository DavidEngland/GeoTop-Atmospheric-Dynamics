# Course Syllabus: Geometric Numerical Analysis for Multiscale Atmospheric Dynamics

## Course Overview & Preserved Structure Hierarchy

This course explores how modern numerical models preserve underlying mathematical structures. Students will learn that every component of a cutting-edge atmospheric model is designed to mirror a specific geometric identity, transforming calculus into exact discrete statements.

| Lecture | Core Topic | Preserved Mathematical Structure |
| --- | --- | --- |
| **Lecture 1** | Foundations of DEC | Topological invariants & Cohomology ($\partial^2=0 \implies d^2=0$) |
| **Lecture 2** | Discrete Differential Geometry on Manifolds | Affine connections, metric compatibility, and parallel transport |
| **Lecture 3** | FEEC & Commuting Diagrams | Operator complexes and the Discrete de Rham Theorem ($\Pi d = d\Pi$) |
| **Lecture 4** | Compatible Discretizations of Primitive Equations | Geostrophic/Hydrostatic balance and mimetic PV relationships |
| **Lecture 5** | Multiscale Dynamics & Fenichel Theory | Fast–slow invariant manifolds ($M_\epsilon$) via Normal Hyperbolicity |
| **Lecture 6** | Objective Material Transport (LCS) | Material transport geometry via Variational & Geodesic LCS |
| **Lecture 7** | Variational & Symplectic Integration | Symplectic structure, momentum maps, and long-term bounded energy |

---

# Detailed Lecture Notes & Refined Frameworks

## Lecture 1: Foundations of Discrete Exterior Calculus (DEC)

### 1. The Tripartite Separation: Topology vs. Geometry vs. Approximation

To prevent the common student pitfall of conflating topological exactness with numerical approximation, the framework must be cleanly divided into three distinct pillars:

* **Topology (The Chain Complex):** Given a primal simplicial complex $K$, the discrete exterior derivative $d_k$ is defined purely combinatorially via the signed incidence matrix of the mesh. Because it mirrors the boundary operator ($\partial \circ \partial = 0$), the coboundary identity:

$$d_{k+1} \circ d_k = 0$$



is **not an approximation**. It is an exact algebraic statement inherited directly from the mesh connectivity, holding down to machine precision regardless of mesh distortion.
* **Geometry (The Metric):** Geometric measurements (lengths, areas, volumes, and inner products) enter the system *exclusively* through the discrete Hodge star ($\star_k$). The Hodge star bridges the primal complex $K$ and its complementary dual complex $\star K$.
* **Approximation (The Mesh Choice):** The numerical error in DEC is entirely born by how we approximate the Hodge star. For example, using a **circumcentric dual** (Delaunay/Voronoi orthogonal duality) yields a simple diagonal Hodge star:

$$\star \omega (\star\sigma^k) = \frac{|\star\sigma^k|}{\|\sigma^k\|} \omega(\sigma^k)$$



This diagonal representation simplifies computation but restricts the approximation to first- or second-order accuracy, sensitive to mesh regularity.

---

## Lecture 2: Discrete Differential Geometry on Manifolds

### 1. The Tangent Bundle Deficit in Pure DEC

Pure DEC provides a beautiful, natural discrete representation of differential forms (cochains), but it **does not by itself provide a canonical representation of tangent vector fields ($T\mathcal{M}$) or contractions between vectors and forms**. The tangent bundle is fundamentally a different geometric object than a chain complex. To handle fluid equations natively written via Lie transport, we must build discrete differential-geometric objects on the physical manifold $\mathcal{M}$ before moving to fluid fluxes.

### 2. Connections, Parallel Transport, and Curvature

Before students can understand Lie transport ($\mathcal{L}_u$), they must master how a vector moves across a curved discrete manifold (like a cubed-sphere or an icosahedral hexagonal grid):

* **Discrete Levi-Civita Connection:** We define a discrete affine connection $\nabla_X Y$ that specifies how vector fields covary along the mesh faces.
* **Discrete Metric Compatibility:** The connection must preserve the discrete inner product of vectors under transport:

$$\delta \langle X, Y \rangle = \langle \nabla_Z X, Y \rangle + \langle X, \nabla_Z Y \rangle$$


* **Parallel Transport & Discrete Curvature:** Moving a vector around a closed loop of simplices reveals the discrete Riemann curvature tensor, manifested as a localized holonomy angle centered at the mesh vertices.

---

## Lecture 3: Finite Element Exterior Calculus (FEEC) & Commuting Diagrams

### 1. The Power of Commuting Projections

When high-order spatial accuracy or flexible meshes (curved elements, $hp$-refinement) are required, we extend DEC into the functional-analytic framework of FEEC. The foundational core of FEEC is the **commuting diagram**:

```
Continuous:   Lambda^k(\mathcal{M}) ────────── d ──────────> Lambda^{k+1}(\mathcal{M})
                  │                                     │
                  │ Pi_k (Projection)                   │ Pi_{k+1}
                  ▼                                     ▼
Discrete:        V_k      ────────── d ──────────>     V_{k+1}

```

The projection operator $\Pi$ maps continuous differential forms to discrete finite element spaces (such as Lagrange, Nédélec, or Raviart-Thomas spaces) such that:


$$\Pi_{k+1} \circ d = d \circ \Pi_k$$

### 2. The Discrete de Rham Theorem

Maintaining $\Pi d = d\Pi$ ensures that the discrete spaces form an exact sequence.

* **Why this is critical:** This property ensures the **Discrete de Rham Theorem** holds. If a discrete form is closed ($d\omega_h = 0$), it is guaranteed to be exact ($\omega_h = d\alpha_h$) up to the topology of the domain. This topological fidelity is what mathematically prevents the appearance of spurious, unphysical pressure modes and grid-aliased instabilities without needing to introduce artificial cross-element filtering.

---

## Lecture 4: Compatible Discretization of the Primitive Equations

### 1. The Rotating Shallow Water Equations (RSWE)

To ground these geometric concepts in actual atmospheric modeling, we apply compatible finite elements to the RSWE in a 2D formulation on the physical manifold $\mathcal{M}$:


$$\partial _t u + (\zeta + f) u^\perp + \nabla \left( g h + \frac{1}{2}|u|^2 \right) = 0$$

$$\partial _t h + \nabla \cdot (hu) = 0$$

Where $u$ is velocity, $h$ is fluid depth, $\zeta = \nabla \times u$ is the relative vorticity, and $f$ is the Coriolis parameter.

### 2. De Rham Mapping for Compatible Dynamical Cores

To ensure accurate structural transport, variables are mapped to the discrete exact sequence that mirrors the continuous 2D rotated de Rham complex:

$$V_0 \xrightarrow{\nabla^\perp} V_1 \xrightarrow{\nabla\cdot} V_2$$

* **Depth ($h \in V_2$):** Modeled using discontinuous $L^2$ elements (2-forms, cell-valued/integrated over areas), ensuring strict mass conservation through the divergence operator.
* **Velocity ($u \in V_1$):** Modeled using $H(\text{div})$ elements (1-forms, edge/face-normal flux degrees of freedom).
* **Vorticity ($\zeta \in V_0$):** A diagnostic scalar recovered by projecting the curl of the $H(\text{div})$ velocity field into continuous $H^1$ space (0-forms, node-valued).

### 3. Mimetic Balance and Discrete Potential Vorticity

* **Spurious PV Mitigation:** Compatible discretizations do not *perfectly* eliminate potential vorticity errors in isolation, but they **substantially reduce spurious PV sources by preserving discrete differential identities and mimetic balance relationships**.
* Because the discrete operators inherit sequence identities exactly, the discrete curl of a gradient term is identically zero ($d^2=0$). This prevents pressure-gradient forcing from acting as a grid-aliased source of vorticity and preserves geostrophic/hydrostatic balances at the discrete level.

---

## Lecture 5: Multiscale Dynamics & Geometric Singular Perturbation Theory (GSPT)

### 1. Fast–Slow Systems & Normal Hyperbolicity

Atmospheric dynamics are governed by multi-scale behaviors where fast inertia-gravity waves coexist with slow, balanced synoptic weather patterns. We express this explicitly as:


$$\begin{aligned}
\frac{dx}{dt} &= f(x, y, \epsilon) \\
\epsilon \frac{dy}{dt} &= g(x, y, \epsilon)
\end{aligned}$$

As $\epsilon \to 0$, the system collapses onto the critical manifold $M_0$. Neil Fenichel’s theorem dictates that this manifold persists as a slow manifold $M_\epsilon$ for $\epsilon > 0$ **if and only if $M_0$ is normally hyperbolic**.

* **The Condition:** Normal hyperbolicity requires that the eigenvalues of the Jacobian of the fast subsystems have non-zero real parts ($\text{Re}\,\lambda_{\text{fast}} \neq 0$).
* If $\text{Re}\,\lambda_{\text{fast}} = 0$, normal hyperbolicity breaks down, leading to bifurcations where the slow manifold can completely disappear or undergo a rapid transition (e.g., canard explosions). A geometric spatial solver prevents grid-induced numerical noise from artificially perturbing these delicate fast eigenvalues.

### 2. Spatial-to-Phase-Space Interaction (Method of Lines)

DEC/FEEC acts on the physical manifold $\mathcal{M}$, not directly on abstract phase space. The rigorous coupling appears after method-of-lines semi-discretization: spatial truncation defects appear in the ODE state equations as grid-dependent forcing terms. By suppressing spurious spatial PV sources and preserving discrete geometric identities, the spatial backbone ensures the induced fast-slow ODE system tracks physical dynamics rather than mesh artifacts. This reduces the risk of numerically induced non-hyperbolic crossings and artificial erosion of the spectral gap ($\text{Re}\,\lambda_{\text{fast}} \neq 0$) supporting persistence of $M_\epsilon$.

---

## Lecture 6: Objective Material Transport via Variational & Geodesic LCS

### 0. Important Pedagogical Note: Phase Space vs. Physical Space

Before defining transport barriers, separate Lecture 5 and Lecture 6 manifold notions explicitly.

* **Fenichel slow manifold ($M_\epsilon$):** lives in abstract state space; one point represents the full atmospheric state (all prognostic fields).
* **Lagrangian coherent structures (LCS):** live in the physical manifold $\mathcal{M}$; they are material curves/surfaces traced by fluid parcels over finite time.

The bridge is conceptual, not an embedding: both use normal attraction/repulsion rates. Haller's variational framework identifies objective physical transport barriers via finite-time normal-repulsion diagnostics, while Fenichel theory uses asymptotic normal hyperbolicity rates to establish persistence of invariant slow manifolds in phase space.

### 1. The Limitation of Standard FTLE

Finite-Time Lyapunov Exponent (FTLE) fields are widely used to visually diagnose atmospheric mixing. However, **FTLE ridges are only heuristic indicators and are not strictly objective**; they can change their shape under time-dependent coordinate transformations (e.g., viewing frames rotating with an atmospheric vortex).

### 2. Objectivity via George Haller’s Variational Theory

To capture true physical transport barriers in jet streams and boundary layers, we introduce **Variational and Geodesic LCS**, which look for coherent invariant structures that are independent of the observer's frame of reference.

[Image showing high FTLE ridges separating distinct fluid mixing zones]

We classify these objective material lines into three categories based on the deformation tensor fields:

* **Hyperbolic LCS:** Extremely sharp, invariant lines that act as generalized stable/unstable manifolds, dictating the structural compression and stretching of air masses.
* **Elliptic LCS:** Coherent vortex boundaries (e.g., the core of an atmospheric river or isolated eddy) where fluid elements experience zero net relative stretching, acting as perfect material traps.
* **Parabolic LCS:** Jet-core shear lines. **Atmospheric jet streams are exceptionally well-described by parabolic LCS**, capturing the exact high-velocity cores that bound global weather systems without relying on arbitrary velocity thresholds.

---

## Lecture 7: Variational & Symplectic Time Integration

### 1. The Energy Misconception vs. Reality

A common misconception is that variational time integrators conserve total system energy exactly. They do not.

* **The Real Behavior:** Variational integrators guarantee **exact preservation of the discrete momentum maps associated with spatial symmetries (via a discrete analogue of Emmy Noether’s theorem) and preserve the symplectic form**.
* **Bounded Energy Error:** Instead of conserving energy exactly at every sub-step, symplectic integrators exhibit a **bounded energy error over exceptionally long integration times**. The system energy oscillates tightly around its true value rather than displaying a systematic, secular drift.

$$\mathcal{H}_{\text{shadow}} = \mathcal{H}_{\text{true}} + \Delta t^2 \mathcal{H}_2 + \Delta t^4 \mathcal{H}_4 + \dots$$

Because they exactly solve a "shadow Hamiltonian" near the true system, they structurally forbid the simulation from slowly gaining or losing energy over multi-decade climate run scales.

---

# Advanced Ph.D. Seminar Verification Questions

### Question 1: Topological Stability vs. Metric Convergence

> **Prompt:** Explain why the discrete exterior derivative identity $d^2=0$ is exact regardless of extreme mesh distortion, whereas the discrete Hodge star ($\star$) generally requires systematic mesh refinement to converge.

* *Expected Answer Key:* $d$ is purely topological; it relies solely on the cell incidence matrix (connectivity), which remains unperturbed by vertex positioning. The Hodge star $\star$ relies on geometric metrics (cell volumes, lengths, and cross-cell dual orthogonal intersections). When a mesh distorts, the circumcentric dual can fall outside its primal element, corrupting the geometric volume ratios and destroying consistency.

### Question 2: Eliminating Spurious Modes via Commuting Projections

> **Prompt:** Prove or visually demonstrate how the commuting diagram property $\Pi d = d\Pi$ mathematically prevents the appearance of spurious checkerboard pressure modes in a shallow water solver.

* *Expected Answer Key:* Spurious modes arise when the gradient operator has a non-trivial, unphysical nullspace (spurious modes hide where $\nabla p = 0$ on the grid but $p \neq 0$). Because $\Pi d = d\Pi$, the discrete nullspaces perfectly mirror the continuous nullspaces. If an element belongs to the nullspace of the continuous derivative, its projection belongs to the discrete nullspace, structurally eliminating any non-physical grid-aliased modes.

### Question 3: Symplectic Bound vs. Runge-Kutta Decay

> **Prompt:** Contrast the energy behavior of a variational integrator with a classical explicit 4th-order Runge-Kutta (RK4) method when applied to a non-linear, inviscid atmospheric flow over a 100-year integration period.

* *Expected Answer Key:* RK4 is not structure-preserving; it introduces sub-step numerical dissipation that manifests as a continuous, secular downward or upward drift in total energy, eventually ruining long-term climate statistics. A variational integrator preserves the symplectic form, meaning the system tracks an exact shadow Hamiltonian. The energy error stays strictly bounded within a small oscillation envelope ($\mathcal{O}(\Delta t^p)$) for all time, exhibiting zero long-term secular drift.
