## 1. The Dual-Time Formulation

To fully capture the dynamics near the transition, we must explicitly state the system in both its fast and slow time formulations. Fenichel theory naturally evaluates stability in the fast system, while the reduced drift is tracked in the slow system.

### Fast-Time System

Let $t_f$ be the fast time. The system is written as:


$$\begin{aligned}
x' &= f(x, y, \epsilon) \\
y' &= \epsilon g(x, y, \epsilon)
\end{aligned}$$


where $' \equiv d/dt_f$.

### Slow-Time System

By rescaling to the slow time $\tau = \epsilon t_f$, the system becomes:


$$\begin{aligned}
\epsilon \dot{x} &= f(x, y, \epsilon) \\
\dot{y} &= g(x, y, \epsilon)
\end{aligned}$$


where $\cdot \equiv d/d\tau$.

---

## 2. Precise Conditions for the Critical Manifold and Generic Fold

Setting $\epsilon = 0$ yields the **critical manifold** $M_0 \subset \mathbb{R}^{n+m}$:


$$M_0 = \{(x,y) \in \mathbb{R}^{n+m} \mid f(x, y, 0) = 0\}$$

### Normal Hyperbolicity

The manifold $M_0$ is **normally hyperbolic** if and only if the spectrum $\sigma$ of the fast Jacobian contains no eigenvalues on the imaginary axis:


$$\sigma\left(D_x f(x, y, 0)\right) \cap i\mathbb{R} = \varnothing$$


When this condition holds, Fenichel theory guarantees that $M_0$ persists as an invariant slow manifold $M_\epsilon$ for $\epsilon > 0$ sufficiently small.

### Generic Fold Conditions

A point $p_0 = (0,0,0)$ defines a generic **saddle-node fold point** (distinguishing it from higher-order degeneracies like cusps) if it satisfies the following non-degeneracy conditions:

1. **Equilibrium:** $f(0,0,0) = 0$
2. **Loss of Hyperbolicity:** $D_x f(0,0,0) = 0$ (a single eigenvalue crosses zero, destroying the spectral gap)
3. **Non-degenerate Curvature:** $D_x^2 f(0,0,0) \neq 0$
4. **Non-vanishing Slow Drift:** $D_y f(0,0,0) \neq 0$

Under these generic conditions, the local Taylor expansion yields the folded saddle-node normal form:


$$\begin{aligned}
x' &= x^2 + y + \mathcal{O}(x^3, xy, y^2, \epsilon) \\
y' &= \epsilon \left(-1 + \mathcal{O}(x, y, \epsilon)\right)
\end{aligned}$$

---

## 3. Geometric Desingularization via the Blow-up Sphere

To resolve the non-hyperbolic point at the origin, we append $\epsilon$ as a state variable ($\epsilon' = 0$) and apply the weighted directional blow-up of Dumortier and Roussarie. The weights are determined by the quasi-homogeneous structure of the fold: $\text{weight}(x)=1$, $\text{weight}(y)=2$, and $\text{weight}(\epsilon)=3$.

The singular origin is replaced by the **blow-up sphere** $S^2 \times [0, r_0]$, where the transformation is defined globally by:


$$x = \bar{x}r, \quad y = \bar{y}r^2, \quad \epsilon = \bar{\epsilon}r^3$$


where $(\bar{x}, \bar{y}, \bar{\epsilon}) \in S^2$ and $r \in [0, r_0]$ is the continuous scaling parameter. This maps the singular point to the boundary sphere $r=0$, allowing us to analyze the atlas of directional charts.

### The Scaling Chart ($K_2$: $\bar{\epsilon} = 1$)

To track the trajectory directly through the singular region, we set $\bar{\epsilon} = 1$, which implies $r = \epsilon^{1/3}$. The local coordinate transformations are:


$$x = \epsilon^{1/3}X, \quad y = \epsilon^{2/3}Y$$

Substituting these into the normal form yields:


$$\begin{aligned}
\epsilon^{1/3} X' &= \epsilon^{2/3}X^2 + \epsilon^{2/3}Y \\
\epsilon^{2/3} Y' &= -\epsilon
\end{aligned}$$

To desingularize the vector field, we divide the system by the common algebraic factor $\epsilon^{1/3}$ and introduce the **desingularized time variable** $s$, defined via the differential transformation:


$$ds = \epsilon^{1/3} dt_f = \epsilon^{-2/3} d\tau$$

This yields the completely desingularized, canonical system in chart $K_2$:


$$\begin{aligned}
\frac{dX}{ds} &= X^2 + Y \\
\frac{dY}{ds} &= -1
\end{aligned}$$

---

## 4. Exact Solutions via the Riccati-Airy Reduction

The desingularized system in $K_2$ can be solved explicitly. From the slow equation, we integrate directly to get $Y(s) = -s$ (assuming an appropriate choice of time origin). Substituting this into the fast equation yields a non-autonomous Riccati equation:


$$\frac{dX}{ds} = X^2 - s$$

We introduce the classic Riccati transformation to linearize the system:


$$X = -\frac{u'}{u}$$

Differentiating $X$ with respect to $s$:


$$\frac{dX}{ds} = -\frac{u''}{u} + \left(\frac{u'}{u}\right)^2 = -\frac{u''}{u} + X^2$$

Equating this to our Riccati equation ($X^2 - s$) yields:


$$-\frac{u''}{u} + X^2 = X^2 - s \implies u'' - su = 0$$

This is precisely the **Airy differential equation**. The solutions for the trajectories tracking the invariant manifold through the fold are dictated by the linear combinations of Airy functions $Ai(s)$ and $Bi(s)$. This rigorous mapping governs the transition before the system exits toward a fast fiber.

---

## 5. Physical Re-Interpretation and Numerical Realities

### The "Vertical Jump" Contextualized

In atmospheric applications, the fast variables $x$ do not explicitly model individual turbulent eddies, but rather the macro-level closure variables of a reduced model (e.g., Turbulent Kinetic Energy $e$, Reynolds shear stresses $\overline{u'w'}$, or eddy viscosity $K_m$).

> **Physical Interpretation:** The passage along the fast fiber after exiting the blow-up region signifies the rapid, structurally enforced collapse of turbulent transport, forcing a swift transition from a weakly stable boundary layer (SBL) to a highly stratified, weakly turbulent or laminar Very Stable Boundary Layer (VSBL).

### Refined Comparison: Singularity vs. Stiffness

| Feature | Standard Numerical View (e.g., WRF) | GSPT + Blow-up View |
| --- | --- | --- |
| **At the Fold Point** | Encounter an under-resolved, highly **stiff regime** where closure parameterizations and fixed timesteps become unreliable. | The origin is blown up to $S^2$; scaling the vector field by $\epsilon^{1/3}$ removes the geometric singularity. |
| **Timescale Treatment** | Experiences numerical "chattering" or artificial oscillations due to scale entanglement. | Separates fast/slow dynamics into independent coordinate charts ($K_1, K_2, K_3$) before gluing solutions back together. |
| **The Transition** | Handled via empirical thresholds or discrete step-changes in stability functions. | Proves a smooth, continuous path for the invariant manifold through the bifurcation via Airy dynamics. |

---

With these corrections, this framework stands ready as a sound foundation for analyzing more complex atmospheric boundary layer phenomena—such as non-autonomous forcing from nocturnal radiative cooling or the appearance of dynamic canard solutions.

Would you like to explore how the inclusion of time-dependent radiative cooling transforms this into a non-autonomous system, or shall we look at how canard solutions manifest in the transition?