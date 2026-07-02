## Homework Problem 1: The Lie Transport Track (Kinematics & Shearing)

### **Problem Statement**

In a neutral, steady-state atmospheric surface layer over a flat grassland ($z_{0,m} = 0.05 \text{ m}$), the horizontal wind field is given by:


$$\mathbf{u} = \left[ \frac{u_*}{\kappa} \ln\left(\frac{z}{z_{0,m}}\right) \right] \hat{\mathbf{i}} + 0\hat{\mathbf{j}} + 0\hat{\mathbf{k}}$$

Suppose a microscopic, field-aligned sensor array is pointing straight up in the vertical direction to measure localized eddy structures. We model this sensor alignment as a geometric vector asset $\mathbf{A} = A_0 \hat{\mathbf{k}}$.

1. Assuming the vector field $\mathbf{A}$ is steady-state ($\frac{\partial \mathbf{A}}{\partial t} = 0$), calculate its material derivative $\frac{D\mathbf{A}}{Dt}$ as it follows the background flow.
2. Calculate the Lie derivative $\mathcal{L}_{\mathbf{u}}\mathbf{A}$ of this vertical asset along the log-stratified velocity field.
3. **Physical Interpretation:** Is the geometric structure of this vertical asset preserved by the boundary layer flow? Based on your answer for $\mathcal{L}_{\mathbf{u}}\mathbf{A}$, explain how the strong surface shear physically deforms a vertical structure as height $z$ approaches the ground.

### **Solution Key for Grading**

1. **Material Derivative:**
$$\frac{D\mathbf{A}}{Dt} = \frac{\partial \mathbf{A}}{\partial t} + (\mathbf{u} \cdot \nabla)\mathbf{A} = 0 + \left[ \frac{u_*}{\kappa}\ln\left(\frac{z}{z_{0,m}}\right)\frac{\partial}{\partial x} \right](A_0 \hat{\mathbf{k}}) = 0$$



*(The physical components do not change along the flat, purely horizontal streamline).*
2. **Lie Derivative:**

$$\mathcal{L}_{\mathbf{u}}\mathbf{A} = \frac{D\mathbf{A}}{Dt} - \frac{\partial \mathbf{A}}{\partial t} - (\mathbf{A} \cdot \nabla)\mathbf{u} = 0 - 0 - \left(A_0 \frac{\partial}{\partial z}\right)\mathbf{u}$$


$$\mathcal{L}_{\mathbf{u}}\mathbf{A} = -A_0 \frac{\partial}{\partial z} \left[ \frac{u_*}{\kappa} \ln\left(\frac{z}{z_{0,m}}\right) \hat{\mathbf{i}} \right] = -\left( \frac{A_0 u_*}{\kappa z} \right) \hat{\mathbf{i}}$$


3. **Interpretation:** Because $\mathcal{L}_{\mathbf{u}}\mathbf{A} \neq 0$, the vertical geometry is *not* invariant under the flow. The negative sign in the $\hat{\mathbf{i}}$ direction means the top of the vector is being dragged faster than the bottom. Because the gradient scales as $1/z$, this tilting and shearing effect becomes drastically more violent the closer the structure gets to the rough surface wall ($z \to 0$).

---

## Homework Problem 2: The Fast-Slow Track (GSPT & Turbulence Relaxation)

### **Problem Statement**

Consider a highly idealized, vertically local model for the evolution of the wind profile gradient $X = \frac{\partial u}{\partial z}$ in the surface layer. The fast timescale dynamics represent turbulent eddy mixing trying to force the atmosphere back to a neutral log-profile equilibrium:


$$\varepsilon \frac{dX}{dt} = -\left( X - \frac{u_*}{\kappa z} \right)$$

Meanwhile, the macroscale background atmosphere experiences a slow diurnal cycle, causing the friction velocity $u_*$ to fluctuate slowly over a period of hours based on a large-scale synoptic pressure gradient:


$$\frac{du_*}{dt} = -\omega \sin(\omega t)$$


where $\varepsilon \ll 1$ represents the rapid turbulent relaxation timescale (seconds) relative to the slow synoptic variations (hours).

1. Identify the **fast variable**, the **slow variable**, and write down the algebraic equation defining the **critical manifold** ($M_0$) for this system by setting $\varepsilon = 0$.
2. State the physical significance of this critical manifold in the context of micrometeorology.
3. If a sudden morning front causes $u_*$ to jump instantly, explain qualitatively how the fast-slow geometry ensures the wind profile relaxes back to a classic logarithmic shape.

### **Solution Key for Grading**

1. **Variables & Manifold:** The fast variable is the wind shear gradient $X$; the slow variable is the friction velocity $u_*$. Setting $\varepsilon = 0$ yields the critical manifold equation:

$$X = \frac{u_*}{\kappa z}$$


2. **Micrometeorological Significance:** The critical manifold $M_0$ is precisely the **neutral logarithmic wind profile profile constraint** from Monin-Obukhov Similarity Theory. It implies that on macroscopic timescales, the boundary layer wind profile is "slaved" to the instantaneous value of the surface friction velocity.
3. **Qualitative Behavior:** Because $\frac{\partial}{\partial X}\left[-(X - \frac{u_*}{\kappa z})\right] = -1 < 0$, the manifold is **normally hyperbolic and strictly attracting**. If $u_*$ shifts, the fast turbulent eddies (acting on the fast timescale) will instantly force the vertical wind gradient $X$ to collapse back onto the attracting manifold, restoring the valid $\ln(z)$ profile almost immediately.