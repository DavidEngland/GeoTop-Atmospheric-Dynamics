### **Course Syllabus: Geometric and Topological Methods in Atmospheric and Fluid Dynamics**

#### **Course Overview**
*   **Level:** Advanced Graduate (Ph.D. / Advanced M.S.).
*   **Philosophy:** This course bridges the gap between **abstract mathematical theory** and **data-driven physical phenomena**, treating differential geometry and topology as the "natural language of continuum physics".
*   **Prerequisites:** Advanced Calculus, Linear Algebra, Ordinary/Partial Differential Equations, and Fluid Mechanics.

---

#### **15-Week Updated Course Outline**

**Unit 1: Differential Geometry and Coordinate-Free Physics**
*   **Week 0: Motivation – Why Geometry Matters:** Side-by-side comparison of "ad-hoc" spherical-coordinate formulations of primitive-equation terms (including Coriolis handling) versus coordinate-free exterior-calculus formulation using wedge products and the Hodge star ($\star$); explicit justification for why the geometric formalism reduces algebraic fragility and improves physical interpretability.
*   **Week 1: Smooth Manifolds and Tangent Spaces:** Differentiable manifolds ($M$); coordinate charts and atlases; the tangent space ($T_pM$) and tangent bundle.
*   **Week 2: Vector Fields, Lie Derivatives, and Flows:** Vector fields as derivations; Lie brackets; streamlines, streaklines, and pathlines in time-dependent atmospheric flows.
*   **Week 3: Differential Forms and Exterior Calculus:** Dual spaces and 1-forms; wedge products; the **exterior derivative ($d$)** as a unified operator for $\nabla$, $\nabla \times$, and $\nabla \cdot$.
*   **Week 4: Integration on Manifolds and Stokes' Theorem:** Orientation; the generalized Stokes’ Theorem; elegant derivation of **Kelvin's Circulation Theorem** and planetary vorticity.
*   **Week 5: Riemannian Geometry and Metric Tensors:** The metric tensor ($g$); connections and covariant differentiation; geodesics and curvature.

**Unit 2: Topology and Coherent Structures**
*   **Week 6: Basics of Algebraic and Differential Topology:** Homotopy and homology; the **Hairy Ball Theorem** and its implications for global wind fields.
*   **Week 7: Morse Theory and Vector Field Topology:** Critical points (nodes, saddles, foci); the Poincaré-Hopf Index Theorem; topological classification of blocking patterns.
*   **Week 8: Lagrangian Coherent Structures (LCS) I:** Introduction to finite-time transport; **Finite-Time Lyapunov Exponents (FTLE)** fields; identifying hyperbolic transport barriers.
*   **Week 9: LCS II – Modern Coherent Structure Detection:** Geodesic LCS; variational methods; applications to **atmospheric rivers**, hurricane eyewalls, and wildfire plumes.

**Unit 3: Dynamics, Bifurcations, and Regime Shifts**
*   **Week 10: Bifurcation Theory and Hysteresis:** Local and global bifurcations (Hopf, Tangent, Cusp); the "Paradox of Enrichment"; the birth of **hysteresis** in nonlinear systems.
*   **Week 11: Climate Tipping Points:** Representing climate components as simplified dynamical systems; **overshoot trajectories** and tipping elements like the Atlantic Thermohaline Circulation.
*   **Week 12: Boundary Layer Geometry:** **Folded equilibrium manifolds** in the nocturnal stable boundary layer; Richardson number geometry; reconstructing stability surfaces from field campaign data.

**Unit 4: Computation, Machine Learning, and Numerical Cores**
*   **Week 13: Modern Geometric Tools (TDA & GML):** **Topological Data Analysis (TDA)** via persistent homology and barcodes; **Geometric Machine Learning** using Graph Neural Networks for weather emulators.
*   **Week 14: Discrete Exterior Calculus (DEC):** Exact conservation as a selection principle; why conventional finite-difference closures can inject artificial dissipation and violate circulation structure; building mimetic numerical cores that preserve topological invariants on **MPAS and ICON grids**.
*   **Week 15: Geometric Numerical Methods & Capstone Presentations:** Symplectic schemes; variational integrators; structure-preserving discretizations for the Navier-Stokes equations.

---

#### **Software Laboratories**
Labs are held bi-weekly to apply theory to **real-world atmospheric datasets** (ERA5, WRF, MPAS output, and CASES-99/Cabauw observations). To reduce tool-friction in a 15-week graduate sequence, laboratories use a **Julia-first computational path** with optional Python equivalents:

| Lab Module | Theoretical Focus | Target Dataset / Model | Primary Tooling |
| --- | --- | --- | --- |
| 1. Kinematic Deformation | Tangent spaces; strain-vs-rotation decomposition | Dual-Doppler radar fields / idealized Rankine vortex | Julia (`DifferentialEquations.jl`, `CairoMakie`) or Python (`xarray`, `SciPy`) |
| 2. Transport Barriers | FTLE fields; hyperbolic LCS | Hurricane eyewall or atmospheric river (ERA5) | Julia (`LagrangianCoherentStructures.jl`) or Python equivalent |
| 3. Bifurcation and Regime Shifts | Folded manifolds; cusp/Hopf bifurcations | Stommel 2-box AMOC model / nocturnal boundary layer collapse | Julia (`BifurcationKit.jl`) with optional `MATCONT` comparison |
| 4. Topological Data Analysis | Persistent homology and barcodes | Convective-cell tracking (MRMS radar / WRF) | Julia (`Eirene.jl`) or Python (`Ripser.py`) |

---

#### **Required Materials & Data Resources**
*   **Software Stack:** Julia as the primary computational environment (`DifferentialEquations.jl`, `BifurcationKit.jl`, `Flux/GeometricFlux`, `Eirene.jl`), with Python companion notebooks (`xarray`, `SciPy`, `Ripser.py`) for interoperability and replication studies; ParaView remains optional for 3D diagnostics.
*   **Reading List:**
    *   *Geometric Mechanics and Symmetry* by Darryl D. Holm.
    *   *Nonlinear Dynamics and Statistical Theories for Oceans and Atmospheres* by Andrew Majda.
    *   *Elements of Applied Bifurcation Theory* by Yuri A. Kuznetsov.
    *   *Mathematical Methods of Classical Mechanics* by Vladimir Arnold (Appendix 2 for geodesic-flow interpretation of ideal fluids).
    *   *Geometric Fluid Dynamics* by Michael Cullen.
    *   Haller, G. (2015), *Lagrangian Coherent Structures*, Annual Review of Fluid Mechanics.
*   **Data Portals:** **Project Pythia** (training), **NASA Earthdata**, and the **Copernicus Climate Data Store** (ERA5).

---

#### **Capstone Project**
In lieu of a final exam, students must complete an original geometric/topological analysis of a research problem, such as the topological evolution of a tornado vortex or a symplectic integration of the shallow-water equations.

#### **Capstone Project Blueprint (Released Week 5)**
To support early scoping and prevent project drift, each team receives a Week 5 blueprint checkpoint and may either propose its own dataset/problem or select one of three structured tracks:

1. **Geometric Track:** Implement a 1D shallow-water solver using DEC and compare its energy/enstrophy conservation to a center-difference baseline.
2. **Topological Track:** Compute persistent homology on climate-simulation fields to quantify topology changes in $Z_{500}$ blocking patterns.
3. **Dynamical Systems Track:** Reconstruct empirical tipping thresholds in a Lorenz-84 style model coupled to a slow ocean component.

Each track requires: (i) a mathematically explicit model statement, (ii) reproducible code and diagnostics, and (iii) a physically interpretable uncertainty/sensitivity discussion.