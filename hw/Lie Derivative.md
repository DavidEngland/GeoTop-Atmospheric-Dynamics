# Lie Derivative in Atmospheric Dynamics

## 1. Why This Operator Matters

The material derivative tracks parcel-following change of a quantity. The Lie derivative additionally captures how geometric objects deform under flow. This is essential when the flow stretches, shears, and rotates structures such as vorticity filaments, fronts, and flux loops.

For a velocity field $\mathbf{u}$ and vector field $\mathbf{A}$,

$$
\mathcal{L}_{\mathbf{u}}\mathbf{A} = [\mathbf{u},\mathbf{A}] = (\mathbf{u}\cdot\nabla)\mathbf{A} - (\mathbf{A}\cdot\nabla)\mathbf{u}.
$$

A useful identity is

$$
\mathcal{L}_{\mathbf{u}}\mathbf{A} = \frac{D\mathbf{A}}{Dt} - \partial_t\mathbf{A} - (\mathbf{A}\cdot\nabla)\mathbf{u}.
$$

So even when $D\mathbf{A}/Dt=0$, geometric deformation can remain nonzero through the stretching and tilting term.

## 2. Frozen-In Criterion

A vector field is frozen into the flow if and only if

$$
\mathcal{L}_{\mathbf{u}}\mathbf{A}=0.
$$

This does not mean $D\mathbf{A}/Dt=0$ in deforming flow; rather, it means the object deforms exactly with the fluid map.

## 3. Differential-Form Perspective

- Mass density can be represented as a volume form $\mu=\rho\,dx\wedge dy\wedge dz$.
- Vorticity is naturally a 2-form.
- Transport laws are compactly written with Lie derivatives and Cartan identities.

This formulation removes coordinate clutter and clarifies conservation structure.

---

## Homework Problems

### Problem 1. Convective Stretching

Let

$$
\mathbf{u}=(0,0,W_0+\sigma z), \qquad \sigma>0,
$$

and let a vertical vortex filament be

$$
\mathbf{B}=B_0\hat{\mathbf{k}}.
$$

Assume steady local state $\partial_t\mathbf{B}=0$ and frozen-in transport $\mathcal{L}_{\mathbf{u}}\mathbf{B}=0$.

1. Compute $D\mathbf{B}/Dt$.
2. Interpret the sign and magnitude physically.

### Problem 2. Uniform Zonal Advection of a Wave-Like Vector Field

Let

$$
\mathbf{u}=U_0\hat{\mathbf{i}}, \qquad
\mathbf{C}=\cos(kx)\hat{\mathbf{j}}.
$$

1. Compute $\mathcal{L}_{\mathbf{u}}\mathbf{C}$ from the Lie bracket definition.
2. Is $\mathbf{C}$ geometrically invariant under this flow?

---

## Solutions

### Solution 1

From

$$
\mathcal{L}_{\mathbf{u}}\mathbf{B} = \frac{D\mathbf{B}}{Dt} - \partial_t\mathbf{B} - (\mathbf{B}\cdot\nabla)\mathbf{u},
$$

and given $\mathcal{L}_{\mathbf{u}}\mathbf{B}=0$ and $\partial_t\mathbf{B}=0$,

$$
\frac{D\mathbf{B}}{Dt}=(\mathbf{B}\cdot\nabla)\mathbf{u}.
$$

Now $(\mathbf{B}\cdot\nabla)=B_0\partial_z$, so

$$
(\mathbf{B}\cdot\nabla)\mathbf{u}=B_0\partial_z(0,0,W_0+\sigma z)=B_0\sigma\hat{\mathbf{k}}.
$$

Hence

$$
\boxed{\frac{D\mathbf{B}}{Dt}=\sigma B_0\hat{\mathbf{k}}.}
$$

Interpretation: the updraft stretching amplifies vertical vorticity-aligned structure.

### Solution 2

Compute each bracket term:

$$
(\mathbf{u}\cdot\nabla)\mathbf{C}=U_0\partial_x\big(\cos(kx)\hat{\mathbf{j}}\big)=-kU_0\sin(kx)\hat{\mathbf{j}},
$$

$$
(\mathbf{C}\cdot\nabla)\mathbf{u}=\cos(kx)\partial_y(U_0\hat{\mathbf{i}})=0.
$$

Therefore

$$
\boxed{\mathcal{L}_{\mathbf{u}}\mathbf{C}=-kU_0\sin(kx)\hat{\mathbf{j}}\neq 0.}
$$

So $\mathbf{C}$ is not geometrically invariant under this uniform advection.
