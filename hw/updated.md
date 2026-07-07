Based on the refined 15-week syllabus, here is a rigorous, advanced graduate-level homework assignment designed to bridge the gap between abstract differential geometry, dynamical systems, and atmospheric data.

This assignment is tailored to be given around **Week 3 to Week 6** (transitioning from Differential Geometry to Topology) or as a comprehensive problem set to test their theoretical foundations before they dive deep into their computational capstone projects.

---

# **Advanced Graduate Homework: Geometric and Topological Methods**

**Course:** Geometric and Topological Methods in Atmospheric and Fluid Dynamics

**Topic:** Exterior Calculus, Kinematic Tensors, and Vector Field Topology

**Expected workload:** This set is intentionally advanced and is calibrated at approximately **17-25 hours** total.

- Problem 1 (Exterior calculus): 4-6 hours
- Problem 2 (Lie derivatives and deformation): 4-5 hours
- Problem 3 (Topology and atmospheric critical points): 3-4 hours
- Problem 4 (ERA5 mini lab): 6-10 hours

---

## **Problem 1: The Coordinate-Free Coriolis Force & The Hodge Star**

In traditional atmospheric dynamics, the Coriolis acceleration on a rotating sphere is written using vector calculus as $2\mathbf{\Omega} \times \mathbf{u}$. In this problem, we will translate this into the coordinate-free language of differential forms on a 2-dimensional smooth manifold $M$ representing the Earth's surface, equipped with a Riemannian metric $g$.

Let $\mathbf{u}$ be the horizontal velocity vector field on the sphere. Let $u^\flat$ be its dual 1-form (under the metric $g$). Let $\omega$ be the volume form (area element) on the sphere, and $\star$ be the Hodge star operator.

1. **Analytical Derivation:** Show that the traditional vector vorticity $\zeta = \nabla \times \mathbf{u} \cdot \hat{\mathbf{k}}$ is fundamentally equivalent to the exterior derivative of the velocity 1-form. Specifically, prove that:

Start by defining

$$\zeta = \star d(u^\flat),$$

and then conclude

$$d(u^\flat) = \zeta \omega$$


2. **The Coriolis 2-Form:** The planetary vorticity can be represented as a 2-form $\Omega = 2\Omega_0 \sin\phi \, \omega$, where $\phi$ is the latitude and $\Omega_0$ is the Earth's angular velocity. Define the Coriolis acceleration 1-form using the interior product (contraction) $i_\mathbf{u}$. Show that:

$$i_\mathbf{u}\Omega = f \star (u^\flat)$$



where $f = 2\Omega_0 \sin\phi$ is the standard Coriolis parameter.
3. **Physical Insight:** Explain in 2–3 sentences why expressing the Coriolis force via the interior product $i_\mathbf{u}\Omega$ is physically superior to the traditional vector cross product when generalizing the equations of motion to non-spherical oblate spheroids or exoplanets.

4. **Coordinate Invariance (short conceptual extension):** In 3-5 sentences, discuss why the differential-form formulation is coordinate invariant and why it extends naturally to arbitrary orientable Riemannian manifolds.

---

## **Problem 1.5 (Bonus): Cartan's Identity and Fluid Kinematics**

Prove Cartan's magic formula for a vector field $X$ and differential form $\alpha$:

$$\mathcal{L}_X\alpha = d\,i_X\alpha + i_X\,d\alpha.$$

Then explain in 4-6 sentences how this identity unifies advection, circulation, and vorticity evolution in geometric fluid dynamics.

---

## **Problem 2: Kinematic Deformation & The Lie Derivative**

Consider a 2D atmospheric flow field describing a tightening frontal zone (deformation field). The velocity field $\mathbf{u} = (u, v)$ in local Cartesian coordinates $(x,y)$ is given by:


$$u = E x, \quad v = -E y$$


where $E > 0$ is the constant stretching deformation rate.

1. **Flow Topology:** Sketch or plot the phase portrait of this vector field. Classify the critical point at $(0,0)$ using standard dynamical systems terminology (e.g., center, saddle, focus, node).
2. **Lie Transport of a Scalar Tracer:** Let $\theta(x, y, t)$ be a potential temperature tracer field. The material derivative (advection) can be coordinate-independently defined via the Lie derivative along the velocity vector field: $\mathcal{L}_\mathbf{u}\theta$.
* First show explicitly that for a scalar field,

$$\mathcal{L}_\mathbf{u}\theta = u(\theta) = u^i\partial_i\theta.$$ 

Then calculate $\mathcal{L}_\mathbf{u}\theta$ for $u=Ex,\; v=-Ey$.
* If $\theta(x,y,0) = \alpha x + \beta y$, solve the transport equation $\frac{\partial \theta}{\partial t} + \mathcal{L}_\mathbf{u}\theta = 0$ analytically to find $\theta(x,y,t)$.


3. **Metric Deformation:** Calculate the Lie derivative of the standard Euclidean metric tensor $g = dx \otimes dx + dy \otimes dy$ along this flow field ($\mathcal{L}_\mathbf{u}g$). Relate the resulting tensor explicitly to the atmospheric **strain rate tensor**.

---

## **Problem 3: The Hairy Ball Theorem and Global Wind Fields**

The Hairy Ball Theorem (Poincaré-Hopf Theorem applied to a 2-sphere $S^2$) states that any continuous tangent vector field on an even-dimensional sphere must have at least one point where the vector field vanishes.

1. **The Euler Characteristic:** State the Euler characteristic $\chi(S^2)$ of a sphere. Write down the Poincaré-Hopf Index Theorem equation relating the indices of critical points $\text{ind}(X, x_i)$ to $\chi(S^2)$.
2. **Meteorological Interpretation:** Imagine a idealized, perfectly smooth global horizontal wind field on Earth during a highly non-linear, stormy season.
2. **Meteorological Interpretation:** Imagine an idealized, perfectly smooth global horizontal wind field on Earth during a highly non-linear, stormy season.
* Is it topologically possible to have a global wind field that consists *entirely* of regular, non-vanishing zonal flow (purely West-to-East winds everywhere, including the poles)? Prove why or why not using the indices of the poles.
* Suppose a global weather map features exactly $N$ ideal cyclonic lows (foci, index $+1$) and $M$ ideal anticyclonic highs (nodes, index $+1$). Assuming no other critical points exist except for saddle points (index $-1$) located at atmospheric col points (blocking patterns), derive a strict algebraic constraint equation for the number of saddles $S$ in terms of $N$ and $M$.
* Apply your formula to the synoptic case $N=6$ cyclones and $M=5$ anticyclones, and compute the required number of saddles.



---

## **Problem 4: Real-Data Mini Lab — Reconstructing a Stability Surface**

*Note: For this problem, you will use the provided Python/Jupyter template utilizing `xarray` and `matplotlib` or `Plotly` along with a subset of ERA5 reanalysis data.*

**Background:** In Unit 3 (Week 12), we study how the nocturnal stable boundary layer undergoes sudden regime shifts (collapsing turbulence) which can be viewed as a **folded equilibrium manifold** (a cusp catastrophe) in the phase space spanned by the Richardson number ($Ri$), the geostrophic wind speed ($G$), and the surface cooling rate ($Q$).

```
       Equilibrium Manifold (Cusp Catastrophe)
                /¯¯¯¯¯¯¯\  <- Continuous Turbulence Regime
               /         \
   U-Turn ---->  \        \  <- Unstable/Hysteresis Region
                  \________\ <- Collapsed Turbulence Regime

```

1. **Data Extraction:** Load the provided ERA5 netCDF file containing a week of stable boundary layer data over the Great Plains. Filter for nighttime hours where the surface buoyancy flux is negative.
2. **Phase Space Embedding:** Plot a 3D scatter plot of the data points where:
* $X$-axis = Surface Wind Speed ($U_{10m}$)
* $Y$-axis = Potential Temperature Gradient ($\Delta\theta$ between 2m and 100m)
* $Z$-axis = Turbulent Kinetic Energy (TKE) or a proxy like the variance of vertical velocity ($\sigma_w^2$)


3. **Quantitative Manifold Diagnostics (required):** Determine whether the point cloud is statistically consistent with a folded equilibrium manifold. You must support your conclusion with **at least two quantitative diagnostics** selected from the list below.

Required menu (choose at least two, more encouraged):
* PCA/SVD spectrum and low-dimensional concentration
* Local density estimation (KDE or neighbor-density proxy)
* Gaussian mixture clustering (multi-regime evidence)
* Local curvature estimate on neighborhood-fitted surfaces
* Nearest-neighbor distance statistics by region
* Conditional variance of TKE given $(U, \Delta\theta)$ bins

4. **Evidence-Based Conclusion:** Replace purely visual claims with a short evidence paragraph (6-10 sentences) stating whether your diagnostics support, weakly support, or do not support a folded-manifold interpretation, and identify at least one source of uncertainty (sampling, noise, nonstationarity, or proxy quality).

---

### **Submission Guidelines**

* **Problems 1–3:** Show all analytical steps clearly. You may use LaTeX formatting for your mathematical proofs.
* **Problem 1.5 (Bonus):** Optional, but can recover points from minor algebraic mistakes elsewhere.
* **Problem 4:** Submit your annotated Jupyter Notebook (`.ipynb`) along with a PDF copy showing your 3D phase-space plots, quantitative diagnostic outputs, and written synthesis.

### **Evaluation Emphasis**

- Mathematical correctness and proof quality (Problems 1-3, Bonus)
- Coordinate-free geometric reasoning (not just coordinate manipulation)
- Reproducible and quantitative analysis in Problem 4
- Clarity of physical interpretation and uncertainty discussion