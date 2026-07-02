This list of homework problems is designed for an advanced graduate course in **Geometric and Topological Methods**, adapting concepts from fluid dynamics, numerical modeling, and biological fast-slow systems into the context of atmospheric science.

### **Unit 1: Differential Geometry & Discrete Exterior Calculus**

**Problem 1: Mapping Atmospheric Variables to $k$-Forms**
Based on the **graded algebra of forms**, identify the correct $k$-form representation for the following variables and explain their physical "degrees of freedom" (d.o.f.):
*   **Pressure ($p$)** and **Potential Temperature ($\theta$)**.
*   **Wind Velocity ($v$)**.
*   **Vorticity ($\omega$)**.
*   *Bonus:* Explain why the **Bernoulli function ($B$)** is treated as a 0-form in the vector-invariant momentum equation.

**Problem 2: The Staggered Grid and Primal/Dual Complexes**
In **Discrete Exterior Calculus (DEC)**, variables are "staggered" between a primal mesh (e.g., Delaunay triangles) and a dual mesh (e.g., Voronoi polygons).
*   If velocity $v$ lives on **dual edges**, where must the pressure $p$ and the vorticity $\omega$ live to ensure the discrete operators are exact?
*   Using **Stokes' Theorem**, prove that the discrete exterior derivative $D$ satisfies $D^2 = 0$ exactly on this mesh.

**Problem 3: Discrete Energy Conservation**
The discrete Lamb vector is defined as $I_v(\omega)$. Prove the **discrete energy identity** $\langle v, I_v(\omega) \rangle_1 = 0$. Explain why this identity is critical for the **unconditional structural stability** of weather models like ICON or MPAS.

---

### **Unit 2: Topology and Coherent Structures**

**Problem 4: Calculating the Finite-Time Lyapunov Exponent (FTLE)**
Given a 2D wind field, fluid parcels are advected from $t_0$ to $t$ to create a **flow map** $F_{t_0}^t(x_0)$.
*   Define the **Cauchy-Green deformation tensor** $C$ in terms of this flow map.
*   If the maximum eigenvalue of $C(x_0)$ is $\lambda_{max}$, write the formula for the FTLE field $\sigma_{t_0}^t(x_0)$.
*   Explain physically why a **ridge** in the backward-time FTLE field acts as an "attracting" structure (e.g., an atmospheric river core).

**Problem 5: Topological Data Analysis (TDA) of Storms**
In **Topological Data Analysis**, we use Betti numbers ($\beta_n$) to classify the organization of convective systems.
*   Interpret what $\beta_0 = 15$ and $\beta_1 = 2$ would mean for a radar reflectivity field of a developing multicellular storm.
*   How might tracking the "lifetime" of a $\beta_1$ feature in a **persistence barcode** serve as a precursor to tornadogenesis?

---

### **Unit 3: Dynamics, Bifurcations, and GSPT**

**Problem 6: The SBL as a Fast-Slow System**
> **Notation Note:** In standard dynamical systems, $u$ and $v$ often denote fast and slow variables. To avoid confusion with zonal ($u$) and meridional ($v$) wind components, we use **Turbulent Kinetic Energy (TKE)** as the fast variable $e$ and **background thermal stratification/cooling** as the slow variable $\theta$.

Treat the **Stable Boundary Layer (SBL)** as a fast-slow system governed by:

$$
\dot{e} = f(e, \theta, \epsilon), \qquad
\dot{\theta} = \epsilon g(e, \theta, \epsilon),
$$

where $0 < \epsilon \ll 1$ is the timescale-separation parameter between rapid turbulent adjustment and slow radiative cooling.

*   **A) Critical Manifold:** Define the **critical manifold ($S_0$)** by setting $\epsilon = 0$. What physical state of the boundary layer does $S_0$ represent?
*   **B) Phase-Space Sketch:** Sketch the **folded equilibrium manifold** in the $(e,\theta)$ plane and identify the **fold point** (saddle-node bifurcation) where the weakly stable SBL collapses into the **Very Stable Boundary Layer (VSBL)**.
*   **C) Hysteresis and Regime Transitions:** Using **hysteresis**, explain why collapse at geostrophic wind speed $U_g = 3\,\mathrm{m\,s^{-1}}$ can require ramp-up to $U_g = 6\,\mathrm{m\,s^{-1}}$ for relaminarized flow to switch back to a fully turbulent state.

> **Hint:** Interpret $S_0$ as the set where TKE production and dissipation are balanced. In your sketch, use $e$ on the vertical axis and $\theta$ (or a stability proxy such as $Ri$) on the horizontal axis. Fast trajectories move approximately vertically toward $S_0$.

**Problem 7: Latitude as a Bifurcation Parameter**
Atmospheric boundary-layer dynamics change structurally with **latitude ($\phi$)**, so latitude can be treated as a global bifurcation parameter.

*   **A) Manifold Topology:** Contrast the topology of the boundary-layer manifold in the **Mid-Latitudes** (folded/bistable regime) versus the **Deep Tropics** (flatter, continuously convective equilibrium).
*   **B) Breakdown of Standard Fenichel Reduction:** Explain why **GSPT** plus local normal-form analysis is required in **Polar Regions**, where trajectories pass through **non-hyperbolic** fold points.

> **Hint:** Fenichel theory assumes normal hyperbolicity. What happens to the fast-subsystem eigenvalue at a fold where SBL collapse occurs, and why does standard regular perturbation fail there?

**Problem 8: Inner and Outer Solutions (Matched Asymptotics for the Evening Transition)**
Use a simplified **TKE decay** proxy for evening transition dynamics:

$$
\epsilon \frac{de}{dt} = -(e-\bar e_0)^2 + (\theta_0-\beta t),
$$

where $\epsilon$ is the small turbulent-adjustment timescale and $\beta t$ is slow linear radiative cooling.

*   **A) Outer Solution:** Compute the **outer solution** $e_{\text{outer}}(t)$ on the slow timescale, assuming the fast variable has relaxed onto the attracting slow manifold.
*   **B) Inner Solution:** Compute the **inner solution** $e_{\text{inner}}(\tau)$ in the initial layer near sunset using fast time $\tau=t/\epsilon$.
*   **C) Asymptotic Matching:** Demonstrate Prandtl matching,

$$
\lim_{t\to 0^+} e_{\text{outer}}(t) = \lim_{\tau\to\infty} e_{\text{inner}}(\tau),
$$

and construct a **composite uniformly valid approximation** for the full evening transition.

> **Hint:** The inner solution captures the immediate post-sunset TKE crash; the outer solution captures the slower nocturnal evolution. Matching enforces smooth overlap between the two asymptotic regimes.

---

### **Unit 4: Synthesis & Applied Research**

**Problem 9: Atmospheric Transport Barriers**
Compare and contrast **Fenichel fibers** and **Lagrangian Coherent Structures (LCS)**.
*   Under what assumptions can unstable Fenichel fibers in a fast-slow reduced model correspond to a repelling LCS in physical space?
*   For a polar-vortex potential-vorticity budget, identify which assumptions are plausible, which are questionable, and what additional diagnostics would be needed before claiming equivalence.
*   Discuss how identifying objective barriers can prevent the **"over-smearing" of pollutant plumes** in air quality models like CMAQ.

**Problem 10: The Blow-up Method**
When a system reaches a **fold point**, it loses **normal hyperbolicity** and standard analysis fails.
*   Describe the basic goal of the **blow-up method**: how does a "clever rescaling" make hidden details of a singularity visible?
*   Why is this method superior to standard linearizations for modeling **abrupt regime shifts** in the climate system?