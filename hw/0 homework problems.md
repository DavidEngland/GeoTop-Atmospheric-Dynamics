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
Treat the **Stable Boundary Layer (SBL)** as a fast-slow system where turbulence ($u$) is the fast variable and radiative cooling ($v$) is the slow variable.
*   Define the **critical manifold ($S_0$)** for the system $\dot{u} = f(u, v, 0)$.
*   Sketch a **folded equilibrium manifold** and identify the **fold point** (saddle-node bifurcation) where the SBL collapses into the **Very Stable Boundary Layer (VSBL)**.
*   Using the concept of **hysteresis**, explain why a boundary layer that collapses at a geostrophic wind of 3 m/s might require 6 m/s to "switch" back to a turbulent state.

**Problem 7: Latitude as a Bifurcation Parameter**
Atmospheric dynamics change structurally with **latitude ($\phi$)**.
*   Contrast the topology of the boundary layer manifold in the **Mid-Latitudes** (folded/bistable) versus the **Deep Tropics** (flat/convective equilibrium).
*   Explain why **Geometric Singular Perturbation Theory (GSPT)** is specifically required to resolve the "non-hyperbolic" folds found in **Polar Regions**.

**Problem 8: Inner and Outer Solutions (Matching)**
Using the example of **enzyme kinetics** (Michaelis-Menten) as a proxy for TKE decay:
*   Calculate the **outer solution** where the fast variable has reached a steady state on the slow manifold.
*   Calculate the **inner solution** for the "initial layer" (the rapid collapse of turbulence at sunset).
*   Demonstrate the **matching principle** to show these two solutions overlap to form a uniformly valid approximation of the night-time transition.

---

### **Unit 4: Synthesis & Applied Research**

**Problem 9: Atmospheric Transport Barriers**
Compare and contrast **Fenichel fibers** and **Lagrangian Coherent Structures (LCS)** [model history].
*   Explain how the union of **unstable Fenichel fibers** forms a "repelling LCS" (a fence) that prevents mixing across the **polar vortex edge** [Model history, 371, 794].
*   Discuss how identifying these objective barriers can prevent the **"over-smearing" of pollutant plumes** in air quality models like CMAQ.

**Problem 10: The Blow-up Method**
When a system reaches a **fold point**, it loses **normal hyperbolicity** and standard analysis fails.
*   Describe the basic goal of the **blow-up method**: how does a "clever rescaling" make hidden details of a singularity visible?
*   Why is this method superior to standard linearizations for modeling **abrupt regime shifts** in the climate system?