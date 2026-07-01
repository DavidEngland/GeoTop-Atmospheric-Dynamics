### **Course Syllabus: Geometric and Topological Methods in Atmospheric and Fluid Dynamics**

#### **Course Overview**
*   **Level:** Advanced Graduate (Ph.D. / Advanced M.S.).
*   **Philosophy:** This course bridges the gap between **abstract mathematical theory** and **data-driven physical phenomena**, treating differential geometry and topology as the "natural language of continuum physics".
*   **Prerequisites:** Advanced Calculus, Linear Algebra, Ordinary/Partial Differential Equations, and Fluid Mechanics.

---

#### **15-Week Updated Course Outline**

**Unit 1: Differential Geometry and Coordinate-Free Physics**
*   **Week 0: Motivation – Why Geometry Matters:** Introduction to coordinate-free thinking; why vector calculus becomes cumbersome on a rotating sphere; examples from Earth’s geometry and turbulence.
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
*   **Week 14: Discrete Exterior Calculus (DEC):** Exact conservation as a selection principle; building numerical cores that respect topological invariants; mimetic discretization on **MPAS and ICON grids**.
*   **Week 15: Geometric Numerical Methods & Capstone Presentations:** Symplectic schemes; variational integrators; structure-preserving discretizations for the Navier-Stokes equations.

---

#### **Software Laboratories**
Labs are held bi-weekly to apply theory to **real-world atmospheric datasets** (ERA5, WRF, MPAS output, and CASES-99/Cabauw observations):
1.  **Trajectory Analysis:** Calculating deformation tensors and strain versus rotation using Doppler radar fields.
2.  **LCS Mapping:** Using the **FTLE Hub** codes (Python/MATLAB) to identify hurricane transport barriers.
3.  **Bifurcation Analysis:** Using **AUTO or MATCONT** to track climate tipping points and regime shifts.
4.  **TDA Lab:** Applying **persistent homology** to detect convective organization in radar reflectivity.

---

#### **Required Materials & Data Resources**
*   **Software Stack:** Julia (for speed/differentiation), Python (SciPy, xarray, PyVista), ParaView (3D visualization), and Jupyter Notebooks.
*   **Reading List:**
    *   *Geometric Mechanics and Symmetry* by Darryl D. Holm.
    *   *Nonlinear Dynamics and Statistical Theories for Oceans and Atmospheres* by Andrew Majda.
    *   *Elements of Applied Bifurcation Theory* by Yuri A. Kuznetsov.
*   **Data Portals:** **Project Pythia** (training), **NASA Earthdata**, and the **Copernicus Climate Data Store** (ERA5).

---

#### **Capstone Project**
In lieu of a final exam, students must complete an original geometric/topological analysis of a research problem, such as the topological evolution of a tornado vortex or a symplectic integration of the shallow-water equations.