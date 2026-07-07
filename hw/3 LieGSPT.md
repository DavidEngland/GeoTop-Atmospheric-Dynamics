### Homework Problem 1: The Lie Transport Track (Kinematics & Shear Tilting)

#### **Problem Statement**

In a neutral, steady-state atmospheric surface layer over a flat, homogeneous surface, Monin-Obukhov Similarity Theory dictates that the vertical shear of the mean horizontal wind is inversely proportional to height:

$$\frac{\partial u}{\partial z} = \frac{u_*}{\kappa z}$$

This yields the classic logarithmic wind profile:

$$\mathbf{u}(z) = \left[ \frac{u_*}{\kappa} \ln\left(\frac{z}{z_{0,m}}\right) \right] \hat{\mathbf{i}} + 0\hat{\mathbf{j}} + 0\hat{\mathbf{k}}$$

Suppose a localized, vertically-oriented coherent structure (such as a buoyant thermal plume or a structural element of an eddy) is represented by a geometric vector asset $\mathbf{A} = A_0 \hat{\mathbf{k}}$.

1. Assuming the vector field $\mathbf{A}$ is locally steady ($\frac{\partial \mathbf{A}}{\partial t} = 0$), calculate its material derivative $\frac{D\mathbf{A}}{Dt}$ as it follows the background flow.
2. Calculate the Lie derivative $\mathcal{L}_{\mathbf{u}}\mathbf{A}$ of this vertical asset along the log-stratified velocity field.
3. **Physical Interpretation:** Is the geometric structure of this vertical asset preserved by the boundary layer flow? Based on your answer for $\mathcal{L}_{\mathbf{u}}\mathbf{A}$, explain how this mechanism physically generates streamwise streaks or roll vortices, and describe what happens to the intensity of this deformation as an air parcel approaches the rough surface ($z \to 0$).

#### **Solution Key & Grading Rubric**

1. **Material Derivative Evaluation:**

$$\frac{D\mathbf{A}}{Dt} = \frac{\partial \mathbf{A}}{\partial t} + (\mathbf{u} \cdot \nabla)\mathbf{A} = 0 + \left[ \frac{u_*}{\kappa}\ln\left(\frac{z}{z_{0,m}}\right)\frac{\partial}{\partial x} \right](A_0 \hat{\mathbf{k}}) = 0$$

*Students must show that because the vector field components do not vary spatially along the horizontal streamline, the material derivative is zero.*
2. **Lie Derivative Computation:**
Using the relationship $\mathcal{L}_{\mathbf{u}}\mathbf{A} = \frac{D\mathbf{A}}{Dt} - \frac{\partial \mathbf{A}}{\partial t} - (\mathbf{A} \cdot \nabla)\mathbf{u}$:

$$\mathcal{L}_{\mathbf{u}}\mathbf{A} = 0 - 0 - \left(A_0 \frac{\partial}{\partial z}\right)\mathbf{u} = -A_0 \frac{\partial}{\partial z} \left[ \frac{u_*}{\kappa} \ln\left(\frac{z}{z_{0,m}}\right) \hat{\mathbf{i}} \right] = -\left( \frac{A_0 u_*}{\kappa z} \right) \hat{\mathbf{i}}$$

1. **Physical Interpretation:**
Because $\mathcal{L}_{\mathbf{u}}\mathbf{A} \neq 0$, the vertical geometry is *not* invariant under the flow. The resulting vector points in the negative streamwise direction ($-\hat{\mathbf{i}}$), demonstrating that the strong vertical wind shear is actively tilting the vertical asset forward. This is the exact kinematic mechanism responsible for generating streamwise streaks and roll vortices out of vertical perturbations. Furthermore, because the gradient scales as $1/z$, this tilting deformation becomes singular and increasingly violent near the wall ($z \to 0$).

---

### Homework Problem 2: The Fast-Slow Track (GSPT with Explicit Mixing-Length Closure)

#### **Problem Statement**

Let us construct an explicit fast-slow system for the local evolution of the vertical wind shear gradient, $X = \frac{\partial u}{\partial z}$, in the surface layer.

The fast-timescale dynamics represent turbulent eddy momentum-flux relaxation. We invoke a mixing-length closure where turbulent eddy viscosity scales with height and shear, $\nu_t = (\kappa z)^2 X$. The deviation of local momentum transport from its steady equilibrium value balances against a rapid turbulent-adjustment timescale $\varepsilon \ll 1$ (seconds):

$$\varepsilon \frac{dX}{dt} = -\left[ (\kappa z)^2 X^2 - u_*^2 \right]$$

Meanwhile, the macroscale background atmosphere experiences a slow diurnal cycle, causing the friction velocity $u_*$ to fluctuate slowly over a period of hours based on a large-scale synoptic pressure gradient:

$$\frac{du_*}{dt} = -\omega \sin(\omega t)$$

where $\omega \sim 10^{-4} \text{ s}^{-1}$ represents the slow synoptic forcing frequency.

1. Identify the **fast variable**, the **slow variable**, and write down the algebraic equation defining the **critical manifold** ($M_0$) for this system by setting $\varepsilon = 0$ (assume $X > 0, u_* > 0$). Show how the mixing-length assumption explicitly yields the Monin-Obukhov log-profile gradient.
2. Evaluate the **normal hyperbolicity** of the critical manifold $M_0$ by computing the Jacobian of the fast subsystem along the manifold. Is the manifold attracting or repelling?
3. If a sudden morning front causes $u_*$ to jump instantly, explain how the fast-slow geometry ensures the boundary layer wind profile rapidly relaxes back to a classic logarithmic shape.

#### **Solution Key & Grading Rubric**

1. **Critical Manifold & Closure Integration:**
The fast variable is the wind shear gradient $X$; the slow variable is the friction velocity $u_*$. Setting $\varepsilon = 0$ yields the algebraic constraint:

$$(\kappa z)^2 X^2 - u_*^2 = 0 \implies (\kappa z)X = u_* \implies X = \frac{u_*}{\kappa z}$$

Replacing $X$ with $\frac{\partial u}{\partial z}$ yields $\frac{\partial u}{\partial z} = \frac{u_*}{\kappa z}$. Integrating this equation with respect to $z$ yields the classic neutral logarithmic wind profile $u(z) = \frac{u_*}{\kappa}\ln(z/z_{0,m})$. The mixing length closure $\ell = \kappa z$ is the load-bearing spatial component that defines the geometry of this manifold.
2. **Normal Hyperbolicity Check:**
Define the fast function $f(X, u_*) = -(\kappa z)^2 X^2 + u_*^2$. The stability is determined by evaluating the partial derivative with respect to the fast variable, $\frac{\partial f}{\partial X}$, along the critical manifold $M_0$:

$$\frac{\partial f}{\partial X} = -2(\kappa z)^2 X$$

Substituting $X = \frac{u_*}{\kappa z}$ into the derivative yields:

$$\left. \frac{\partial f}{\partial X} \right|_{M_0} = -2(\kappa z)^2 \left( \frac{u_*}{\kappa z} \right) = -2\kappa z u_*$$

Since $\kappa, z, u_* > 0$, the eigenvalue is strictly negative: $-2\kappa z u_* < 0$. Therefore, the critical manifold $M_0$ is **normally hyperbolic and strictly attracting**.
3. **Qualitative Dynamical Behavior:**
Because the manifold is strongly attracting, any sudden synoptic disruption to $u_*$ instantly knocks the system off $M_0$ into the fast blue sky of the state space. The fast turbulent eddies (acting on the $O(\varepsilon)$ timescale) will rapidly force the vertical wind gradient $X$ to collapse vertically back down onto the attracting manifold $M_0$. Once trapped back on the manifold, the profile instantly satisfies the logarithmic configuration again, tracking any subsequent slow adjustments to $u_*$ along the slow timescale.

---

