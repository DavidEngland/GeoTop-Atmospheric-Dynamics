# Course Syllabus & Lesson Plan Overview

**Course Title:** Geometric Numerical Analysis for Multiscale Atmospheric Dynamics

**Target Audience:** Advanced Ph.D. students in Computational Physics, Applied Mathematics, or Atmospheric Science.

**Prerequisites:** Differential Geometry, Numerical PDEs, and Dynamical Systems Theory.

## Implementation Alignment Notes (2026 Refresh)

1. **Week 0 to Week 1 Bridge:** Open with a direct comparison between coordinate-heavy spherical primitive-equation manipulations and coordinate-free exterior-calculus formulations to motivate the manifold and tangent-bundle formalism.
2. **Lab Tooling Policy:** Core labs are Julia-first (with optional Python parity notebooks) to avoid multi-environment overhead during the 15-week timeline.
3. **DEC Pedagogical Anchor:** Explicitly connect Week 14 content to circulation/structure preservation, emphasizing why mimetic geometry-preserving schemes are not interchangeable with standard dissipative discretizations.
4. **Capstone Scaffolding:** Release a Week 5 project blueprint checkpoint so teams can commit early to one of three tracks (Geometric, Topological, Dynamical Systems) or submit an approved custom track.

| Lecture | Core Topic | Geometric Objective | Mathematical Focus |
| --- | --- | --- | --- |
| **Lecture 1** | Foundations of DEC | Splitting topology and metric | Cochains, Exact Coboundary ($d^2=0$), Diagonal Hodge Star |
| **Lecture 2** | The Tangent Bundle Barrier | Moving from forms to vector transport | Cartan’s Formula, Discrete Lie Derivatives, FEEC |
| **Lecture 3** | Multiscale Scales & GSPT | Isolating the atmospheric slow manifold | Fenichel Theory, Froude/Rossby expansion, Canards |
| **Lecture 4** | Kinematic Boundaries (LCS) | Mapping transport barriers in discrete flows | Finite-Time Lyapunov Exponents (FTLE), Flow Foliations |
| **Lecture 5** | Unification & Time-Stepping | Closing the system without energy drift | Variational & Symplectic Integrators, Discrete Hamilton's Principle |

---

# Detailed Lecture Notes

## Lecture 1: Foundations of Discrete Exterior Calculus (DEC)

### 1. The Core Philosophy

Traditional numerical methods (Finite Difference, Finite Volume) approximate differential operators using Taylor series expansions. When the grid warps or refines, these expansions introduce truncation errors that break fundamental vector calculus identities (e.g., $\nabla \cdot (\nabla \times \vec{A}) \neq 0$).

DEC solves this by separating **topology** (how cells connect) from **metric** (how big cells are).

### 2. Topological Chain Complexes

We discretize our spatial manifold $M$ into a primal simplicial complex $K$ (e.g., a Delaunay triangulation) and an orthogonal circumcentric dual complex $\star K$ (e.g., a Voronoi tessellation).

* **$k$-simplices ($\sigma^k$):** Nodes ($k=0$), Edges ($k=1$), Faces ($k=2$), Volumes ($k=3$).
* **$k$-cochains:** Linear functionals that evaluate a field by integrating it over a $k$-simplex. They are the discrete analogues of differential forms.

The continuous exterior derivative $d$ maps $k$-forms to $(k+1)$-forms. Its discrete counterpart is the **coboundary operator $d_k$**, which is defined *purely combinatorially* as the signed incidence matrix of the mesh.

> **Theorem (Exact Topology):** Because $d_k$ is defined strictly by mesh connectivity, the fundamental identity:
>
> $$d_{k+1} \circ d_k = 0$$
>
>
>
> holds **exactly** down to machine precision. As a result, Stokes' theorem is algebraically exact on the mesh:
>
> $$\langle d_k \omega, c \rangle = \langle \omega, \partial c \rangle$$
>
>

### 3. The Metric Metric Gatekeeper: The Hodge Star

Metric information (lengths, areas, volumes) enters solely through the **Discrete Hodge Star ($\star$)**, which maps a primal $k$-cochain to a dual $(n-k)$-cochain. In a diagonal approximation:

$$\star \omega (\star\sigma^k) = \frac{|\star\sigma^k|}{|\sigma^k|} \omega(\sigma^k)$$

Where $|\cdot|$ represents the geometric measure. **All spatial numerical truncation error in pure DEC originates here.**

---

## Lecture 2: The Tangent Bundle Barrier & FEEC

### 1. The Breakdown of Pure DEC in Atmospheric Dynamics

While DEC handles static differential forms beautifully, atmospheric equations are advective. They describe fluid moving along velocity vector fields in the **tangent bundle ($TM$)**.

The material derivative of an atmospheric differential form $\omega$ along a velocity vector field $u$ is governed by the **Lie derivative ($\mathcal{L}_u$)**, expressed via Cartan's magic formula:

$$\mathcal{L}_u \omega = d(i_u \omega) + i_u (d\omega)$$

Where $i_u$ is the interior product (contraction). Computing $i_u \omega$ in pure DEC is poorly defined because it requires multiplying a vector field (defined on tangent spaces) with a cochain (integrated over elements), requiring clumsy spatial interpolations that ruin conservation laws.

### 2. The Finite Element Exterior Calculus (FEEC) Solution

To preserve the structural benefits of DEC while properly resolving the tangent bundle, we move to **FEEC**. Instead of mapping variables to discrete simplices, FEEC maps them to specific, structure-preserving polynomial function spaces within a continuous De Rham complex:

$$0 \rightarrow H^1 \xrightarrow{\nabla} H(\text{curl}) \xrightarrow{\nabla\times} H(\text{div}) \xrightarrow{\nabla\cdot} L^2 \rightarrow 0$$

* **0-forms (Pressure/Potential):** Modeled using continuous Lagrange elements ($H^1$).
* **1-forms (Velocity/Circulation):** Modeled using Nédélec edge elements ($H(\text{curl})$).
* **2-forms (Vorticity/Flux):** Modeled using Raviart-Thomas face elements ($H(\text{div})$).

By leveraging these precise polynomial basis functions, we can construct stabilized, upwinded discrete Lie derivatives ($\mathcal{L}_u$). This tracks advection accurately over curved surfaces (like the Earth's sphere) while preserving the underlying topological exactness ($d^2=0$).

---

## Lecture 3: Geometric Singular Perturbation Theory (GSPT) in the ABL

### 1. The Multiscale Problem

Atmospheric flow—particularly in the Atmospheric Boundary Layer (ABL)—contains highly disparate timescales. Fast, high-frequency acoustic and gravity waves mix with the slow, balanced geostrophic and hydrostatic convective structures.

Treating this with standard explicit time-stepping requires tiny time steps to satisfy the CFL condition, which introduces crippling numerical dissipation.

### 2. Fast-Slow Decomposition

We frame the atmospheric system as a fast-slow explicit system using a small dimensionless scale parameter $\epsilon$ (e.g., the Rossby or Froude number):

$$\begin{aligned}
\frac{dx}{dt} &= f(x, y, \epsilon) \quad (\text{Slow Dynamics}) \\
\epsilon \frac{dy}{dt} &= g(x, y, \epsilon) \quad (\text{Fast Dynamics})
\end{aligned}$$

When $\epsilon \to 0$, the fast dynamics collapse onto a **critical manifold** $M_0 = \{(x,y) \mid g(x,y,0) = 0\}$.

### 3. Fenichel Theory & The Spatial Connection

According to **Fenichel's Theorem**, if $M_0$ is normally hyperbolic, then for a sufficiently small $\epsilon > 0$, there exists a persistent **slow manifold $M_\epsilon$** that tracks the slow, balanced evolution of the atmosphere.

* **The Geometric Synergy:** If your underlying spatial solver uses a non-geometric method, numerical dissipation will artificially alter $\epsilon$ or introduce non-physical perturbations that knock the state vector off $M_\epsilon$.
* By using **DEC/FEEC** as the spatial backbone, the unphysical generation of potential vorticity is eliminated. The simulation stays locked directly to the mathematically true slow manifold, allowing for accurate tracking of sudden transitions like boundary layer separations (canard explosions).

---

## Lecture 4: Lagrangian Coherent Structures (LCS)

### 1. Diagnosing Material Transport

Once our spatial (DEC/FEEC) and multiscale (GSPT) layers generate clean velocity fields, we must diagnose the actual mixing boundaries, transport barriers, and pollutant trapping zones within the fluid. This is done via **LCS**.

LCS are the finite-time analogues of invariant manifolds (stable and unstable manifolds) in non-autonomous dynamical systems.

### 2. Mathematical Extraction via FTLE

To find these hidden geometric barriers, we compute the **Finite-Time Lyapunov Exponent (FTLE)**. We seed a field of tracer particles and flow them forward (or backward) in time using our advective velocity fields.

Let $\phi_{t_0}^{t_0 + T}(x)$ be the flow map taking a particle from position $x$ at time $t_0$ to its position at $t_0 + T$. The Right Cauchy-Green deformation tensor is:

$$\Delta = \left( \frac{\partial \phi_{t_0}^{t_0+T}(x)}{\partial x} \right)^T \left( \frac{\partial \phi_{t_0}^{t_0+T}(x)}{\partial x} \right)$$

The maximum eigenvalue of this tensor, $\lambda_{\max}(\Delta)$, measures the maximum separation between adjacent particles. The FTLE field is defined as:

$$\text{FTLE}(x, t_0, T) = \frac{1}{|T|} \ln \sqrt{\lambda_{\max}(\Delta)}$$

[Image showing high FTLE ridges separating distinct fluid mixing zones]

* **Ridges as Barriers:** Maximizing ridges of the **forward-time FTLE** act as repelling material lines (unstable manifolds), while ridges of the **backward-time FTLE** act as attracting material lines (stable manifolds).
* **The Integration:** Because the Lie transport in Layer 2 does not suffer from artificial grid-aligned numerical diffusion, the resulting FTLE ridges remain exceptionally sharp and physically accurate, allowing scientists to track marine fronts or chemical plumes perfectly.

---

## Lecture 5: Symplectic & Variational Integration

### 1. Temporal Energy Drift

Even with perfect spatial discretization (DEC/FEEC) and accurate scale separation (GSPT), standard time-stepping schemes (like Runge-Kutta 4) introduce a subtle, unphysical energy drift over long integration periods. This occurs because they do not preserve the symplectic structure of the system's phase space.

### 2. Discrete Hamilton's Principle

To achieve a completely structure-preserving engine, the final layer uses a **variational integrator**. Instead of discretizing the continuous differential equations in time, we discretize the **Lagrangian action integral** itself:

$$S = \int_{0}^{T} L(q, \dot{q}) \, dt \quad \longrightarrow \quad S_d = \sum_{k=0}^{N-1} L_d(q_k, q_{k+1}, \Delta t)$$

We then look for stationary points of this discrete action by setting the discrete variations to zero ($\delta S_d = 0$), yielding the **Discrete Euler-Lagrange (DEL) equations**:

$$D_2 L_d(q_{k-1}, q_k, \Delta t) + D_1 L_d(q_k, q_{k+1}, \Delta t) = 0$$

> **The Architectural Payoff:** By updating states via the DEL equations, the time-stepping algorithm automatically inherits **Noether's Theorem** at the discrete level. Total energy, momentum, and enstrophy are conserved globally for centuries of simulation time without any ad-hoc artificial filtering.

---

# Verification & Seminar Discussion Prompts

To wrap up this module, use these analytical questions to test the conceptual integration of these tools:

1. **The Core Tension:** Why does the diagonal Hodge star in DEC introduce numerical error, while the discrete exterior derivative $d$ remains perfectly exact? How does a regular Delaunay mesh minimize this error?
2. **The Coupling Failure Mode:** If you couple a pure DEC spatial solver with a non-symplectic time integrator (like forward Euler), what happens to the slow manifold ($M_\epsilon$) over an extended 50-year climate simulation?
3. **The Lagrangian Dilemma:** Explain how a high-order FEEC space (like Raviart-Thomas elements) simplifies the evaluation of the interior product $i_u \omega$ in Cartan's formula compared to standard node-centered finite differences.