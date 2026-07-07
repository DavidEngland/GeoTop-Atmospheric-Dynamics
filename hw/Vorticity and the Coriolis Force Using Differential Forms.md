# Graduate Homework Problem: Vorticity and the Coriolis Force Using Differential Forms

**Course:** Geometric and Topological Methods in Atmospheric Dynamics  
**Topic:** Exterior calculus on two-dimensional Riemannian manifolds

---

## Problem

Let $(M,g)$ be an oriented two-dimensional Riemannian manifold with metric $g$, area form $\omega$, and Hodge star operator $\star$. Let $\mathbf{u}$ be a velocity vector field, and let $u^\flat$ denote its metric-dual 1-form.

Answer the following.

### (a) Exterior Derivative and Scalar Vorticity

Show that the exterior derivative $d(u^\flat)$ can be written uniquely as

$$
d(u^\flat)=\zeta\,\omega,
$$

for some smooth scalar field $\zeta$.

Then prove that

$$
\boxed{\zeta=\star d(u^\flat).}
$$

Finally, verify that in local Cartesian coordinates,

$$
u^\flat=u_x\,dx+u_y\,dy,
$$

this definition reduces to

$$
\zeta=\frac{\partial u_y}{\partial x}-\frac{\partial u_x}{\partial y}.
$$

### (b) Coriolis Acceleration as an Interior Product

Suppose the planetary vorticity 2-form is

$$
\Omega=f\,\omega,
$$

where

$$
f=2\Omega_0\sin\phi
$$

is the Coriolis parameter.

Using the definition of the interior product,

$$
(i_{\mathbf u}\Omega)(X)=\Omega(\mathbf u,X),
$$

show that

$$
\boxed{i_{\mathbf u}\Omega=f\,\star u^\flat.}
$$

### (c) Coordinate-Free Interpretation

Explain why

$$
d(u^\flat)=\zeta\,\omega,
\qquad
i_{\mathbf u}\Omega=f\,\star u^\flat,
$$

is more geometrically fundamental than

$$
\nabla\times\mathbf u,
\qquad
f\,\hat{\mathbf k}\times\mathbf u.
$$

Discuss intrinsic geometry and coordinate invariance.

---

## Solution

### (a) Vorticity as the Exterior Derivative

Since $M$ is oriented and two-dimensional, each tangent space has a non-vanishing area form $\omega$. Also,

$$
\Lambda^2(T_p^*M)=\operatorname{span}\{\omega_p\},
$$

so every 2-form can be written uniquely as $\alpha=\phi\,\omega$ for some scalar $\phi$.

Because $d(u^\flat)$ is a 2-form, there exists a unique scalar field $\zeta$ such that

$$
d(u^\flat)=\zeta\,\omega.
$$

On a two-dimensional oriented Riemannian manifold, $\star\omega=1$. Applying $\star$ to both sides gives

$$
\star d(u^\flat)=\star(\zeta\omega)=\zeta\,\star\omega=\zeta,
$$

hence

$$
\boxed{\zeta=\star d(u^\flat).}
$$

In Cartesian coordinates,

$$
u^\flat=u_x\,dx+u_y\,dy,
$$

so

$$
\begin{aligned}
d(u^\flat)
&=d(u_x)\wedge dx+d(u_y)\wedge dy \\
&=\left(\frac{\partial u_y}{\partial x}-\frac{\partial u_x}{\partial y}\right)dx\wedge dy.
\end{aligned}
$$

Since $\omega=dx\wedge dy$,

$$
d(u^\flat)=\left(\frac{\partial u_y}{\partial x}-\frac{\partial u_x}{\partial y}\right)\omega.
$$

Applying $\star$ yields

$$
\boxed{\zeta=\frac{\partial u_y}{\partial x}-\frac{\partial u_x}{\partial y}},
$$

which is the vertical component of curl:

$$
\zeta=(\nabla\times\mathbf u)\cdot\hat{\mathbf k}.
$$

### (b) The Coriolis 2-Form

The planetary vorticity 2-form is

$$
\Omega=f\,\omega.
$$

By definition,

$$
(i_{\mathbf u}\Omega)(X)=\Omega(\mathbf u,X)=f\,\omega(\mathbf u,X).
$$

For any 1-form $\alpha$,

$$
(\star\alpha)(X)=\omega(\alpha^\sharp,X),
$$

where $\alpha^\sharp$ is the metric-dual vector field. Setting $\alpha=u^\flat$, we have $(u^\flat)^\sharp=\mathbf u$, so

$$
(\star u^\flat)(X)=\omega(\mathbf u,X).
$$

Therefore,

$$
(i_{\mathbf u}\Omega)(X)=f(\star u^\flat)(X).
$$

Since this holds for every vector field $X$,

$$
\boxed{i_{\mathbf u}\Omega=f\,\star u^\flat.}
$$

This is the intrinsic differential-geometric form of Coriolis acceleration.

### (c) Geometric Interpretation

The differential-form formulation is intrinsic to the manifold and uses only:

- the metric $g$,
- orientation,
- the exterior derivative $d$,
- the Hodge star $\star$, and
- the interior product $i_{\mathbf u}$.

Unlike $f\,\hat{\mathbf k}\times\mathbf u$, it does not require an embedding into $\mathbb{R}^3$. That matters on curved surfaces (oblate spheroids, tidally distorted bodies, or irregular geometries), where a globally defined ambient vertical $\hat{\mathbf k}$ is not naturally available.

Moreover, $d$, $i_{\mathbf u}$, and $\wedge$ are coordinate independent. Under coordinate changes, forms transform naturally via pullbacks without changing the equation structure. The Hodge star is metric-dependent, but precisely in the intrinsic way needed for the local geometry.

Therefore,

$$
d(u^\flat)=\zeta\,\omega,
\qquad
i_{\mathbf u}\Omega=f\,\star u^\flat,
$$

is valid on any oriented two-dimensional Riemannian manifold.

---

## Learning Objectives

After completing this problem, students should be able to:

1. Express scalar vorticity using exterior calculus.
2. Use the Hodge star to connect differential forms with classical vector calculus.
3. Derive the intrinsic geometric form of Coriolis acceleration.
4. Explain why differential forms provide a coordinate-free framework for atmospheric dynamics on curved surfaces.
