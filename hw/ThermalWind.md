# Homework Problem: Thermal Wind via Exterior Calculus

Course: Geometric and Topological Methods in Atmospheric Dynamics  
Topic: Thermal wind balance on a stratified rotating manifold

## Problem Statement

Let

$$
M = \Sigma \times \mathbb{R},
$$

where $\Sigma$ is an oriented two-dimensional Riemannian manifold (horizontal planetary surface) with metric $g_\Sigma$, area form $\omega_\Sigma$, and Hodge star $\star_\Sigma$, and $z \in \mathbb{R}$ is the vertical coordinate.

Let

- $u^\flat$ be the horizontal velocity 1-form,
- $\mathbf{u} = (u^\flat)^\sharp$ the horizontal velocity vector field,
- $p$ pressure,
- $\rho$ density,
- $b$ buoyancy,
- $f$ Coriolis parameter,
- $d_\Sigma$ the horizontal exterior derivative.

Use the decomposition of the full exterior derivative:

$$
d = d_\Sigma + dz \wedge \partial_z.
$$

## Part A. Geostrophic and Hydrostatic Balance in 1-Form Language

Assume steady, inviscid, hydrostatic-geostrophic balance under a Boussinesq scaling:

$$
f\,\star_\Sigma u^\flat = -\frac{1}{\rho_0} d_\Sigma p,
$$

$$
\partial_z p = -\rho_0 b.
$$

1. Show that

$$
\frac{1}{\rho_0}dp = -f\,\star_\Sigma u^\flat - b\,dz.
$$

2. Briefly explain why this single equation is a compact geometric encoding of both horizontal geostrophic balance and vertical hydrostatic balance.

## Part B. Thermal Wind from Nilpotency ($d^2=0$)

Apply $d$ to

$$
\frac{1}{\rho_0}dp = -f\,\star_\Sigma u^\flat - b\,dz.
$$

Using $d^2p=0$, $\partial_z f=0$, and graded-commutativity of the wedge product:

1. Separate horizontal 2-form terms from mixed $dz \wedge (\cdot)$ terms.
2. Derive the intrinsic thermal wind relation

$$
\boxed{f\,\star_\Sigma(\partial_z u^\flat) = d_\Sigma b.}
$$

Hint: Use $dz \wedge dz = 0$ and the fact that $\star_\Sigma$ acts only on horizontal forms.

## Part C. Physical Interpretation

1. Interpret $\star_\Sigma(\partial_z u^\flat)$ physically. For a poleward buoyancy gradient, what is the implied orientation of vertical shear?
2. Compare

$$
f\,\star_\Sigma(\partial_z u^\flat)=d_\Sigma b
$$

with the classical vector form

$$
f\,\partial_z \mathbf{u} = \hat{\mathbf{k}} \times \nabla b.
$$

Explain why the differential-form formulation is cleaner on non-spherical planets.

## Part D. Baroclinic Generalization

Without Boussinesq simplification in the horizontal momentum balance, take

$$
f\,\star_\Sigma u^\flat = -\frac{1}{\rho}d_\Sigma p.
$$

1. Apply $d_\Sigma$ and prove

$$
\boxed{d_\Sigma(f\,\star_\Sigma u^\flat)=\frac{1}{\rho^2}d_\Sigma \rho \wedge d_\Sigma p.}
$$

2. Explain the geometric and physical meaning of $d_\Sigma\rho \wedge d_\Sigma p$.
3. State what condition corresponds to barotropic flow in this language.

---

## Complete Solution

### A. Compact balance equation

From

$$
dp = d_\Sigma p + (\partial_z p)dz,
$$

substitute geostrophic and hydrostatic balances:

$$
\frac{1}{\rho_0}d_\Sigma p = -f\,\star_\Sigma u^\flat,
\qquad
\frac{1}{\rho_0}(\partial_z p)dz = -b\,dz.
$$

Adding both pieces gives

$$
\boxed{\frac{1}{\rho_0}dp = -f\,\star_\Sigma u^\flat - b\,dz.}
$$

This equation is compact because its horizontal component is geostrophic balance and its vertical component is hydrostatic balance.

### B. Thermal wind derivation

Apply $d$ to both sides:

$$
0=d\!\left(-f\,\star_\Sigma u^\flat - b\,dz\right).
$$

Compute each contribution.

1. First term:

$$
d(f\,\star_\Sigma u^\flat)
= d_\Sigma(f\,\star_\Sigma u^\flat) + dz\wedge \partial_z(f\,\star_\Sigma u^\flat).
$$

Since $\partial_z f=0$,

$$
\partial_z(f\,\star_\Sigma u^\flat)=f\,\partial_z(\star_\Sigma u^\flat).
$$

2. Second term:

$$
d(b\,dz)=db\wedge dz
=(d_\Sigma b + (\partial_z b)dz)\wedge dz
=d_\Sigma b\wedge dz
=-dz\wedge d_\Sigma b.
$$

Therefore

$$
0 = -d_\Sigma(f\,\star_\Sigma u^\flat)
-dz\wedge f\,\partial_z(\star_\Sigma u^\flat)
+dz\wedge d_\Sigma b.
$$

Separate form types.

- Horizontal 2-form compatibility:

$$
d_\Sigma(f\,\star_\Sigma u^\flat)=0.
$$

- Mixed terms:

$$
-dz\wedge f\,\partial_z(\star_\Sigma u^\flat) + dz\wedge d_\Sigma b = 0.
$$

Hence

$$
f\,\partial_z(\star_\Sigma u^\flat)=d_\Sigma b.
$$

Because $\star_\Sigma$ is horizontal,

$$
\partial_z(\star_\Sigma u^\flat)=\star_\Sigma(\partial_z u^\flat).
$$

So the thermal wind relation is

$$
\boxed{f\,\star_\Sigma(\partial_z u^\flat)=d_\Sigma b.}
$$

### C. Interpretation

The operator $\star_\Sigma$ rotates a horizontal 1-form (or vector) by $90^\circ$ with respect to orientation on $\Sigma$. Thus thermal wind says buoyancy gradients are in rotated balance with vertical wind shear.

If buoyancy increases poleward, the vertical shear is primarily zonal. In Earth-like orientation, this implies stronger westerlies aloft in midlatitudes.

Compared with $\hat{\mathbf{k}}\times\nabla b$, the form-based equation is intrinsic: no ambient 3D embedding and no globally defined Euclidean cross product are required.

### D. Baroclinic term

Start from

$$
f\,\star_\Sigma u^\flat = -\frac{1}{\rho}d_\Sigma p.
$$

Apply $d_\Sigma$:

$$
d_\Sigma(f\,\star_\Sigma u^\flat)
= -d_\Sigma\!\left(\frac{1}{\rho}d_\Sigma p\right)
= -d_\Sigma\!\left(\frac{1}{\rho}\right)\wedge d_\Sigma p
-\frac{1}{\rho}d_\Sigma^2 p.
$$

Since $d_\Sigma^2 p=0$,

$$
d_\Sigma(f\,\star_\Sigma u^\flat)
= -d_\Sigma\!\left(\frac{1}{\rho}\right)\wedge d_\Sigma p.
$$

Using

$$
d_\Sigma\!\left(\frac{1}{\rho}\right) = -\frac{1}{\rho^2}d_\Sigma\rho,
$$

we obtain

$$
\boxed{d_\Sigma(f\,\star_\Sigma u^\flat)=\frac{1}{\rho^2}d_\Sigma\rho\wedge d_\Sigma p.}
$$

The 2-form $d_\Sigma\rho\wedge d_\Sigma p$ measures non-alignment of density and pressure gradients. If it vanishes, gradients are locally parallel, isopycnals align with isobars, and the state is barotropic (no baroclinic vorticity generation term).

---

## Learning Objectives

After this assignment, you should be able to:

1. Express geostrophic and hydrostatic balance in one differential-form equation.
2. Derive thermal wind from exterior-calculus structure ($d^2=0$), not ad hoc curl algebra.
3. Interpret thermal wind geometrically through the horizontal Hodge star.
4. Connect baroclinicity to wedge products of thermodynamic gradients.
