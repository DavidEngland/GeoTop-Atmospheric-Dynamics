# Additional Advanced Homework Problems

This file provides optional extension problems for students who want deeper preparation for research in geometric fluid dynamics.

## Problem A. Potential Vorticity as a Lie-Transported Form

Define the absolute-vorticity 2-form on a rotating manifold by

$$
\omega_a = d u^\flat + \Omega,
$$

and potential temperature by $\theta$.

1. Show that for inviscid, adiabatic flow, the 3-form

$$
Q = \omega_a \wedge d\theta
$$

is Lie transported.
2. Explain the connection to Ertel potential vorticity conservation.
3. State the assumptions under which this conservation can fail.

## Problem B. Rossby-Wave Geometry from Differential Forms

Starting from barotropic vorticity transport,

$$
\partial_t \zeta + \mathbf{u}\cdot\nabla(\zeta + f)=0,
$$

recast the dynamics in intrinsic form on an oriented surface $\Sigma$.

1. Interpret $df$ as the intrinsic beta-parameter 1-form.
2. Explain how geometry modifies wave propagation on non-spherical planets.
3. Compare this intrinsic formulation to the standard beta-plane approximation.

## Problem C. Frontogenesis in Coordinate-Free Form

Let $T$ be temperature and $dT$ its gradient 1-form.

1. Derive an expression for the evolution of $|dT|^2$ under advection and deformation.
2. Relate the result to the symmetric strain tensor.
3. Explain why frontogenesis corresponds to metric compression of $dT$.

## Problem D. Discrete Exterior Calculus and Conservation

On an unstructured primal-dual mesh, let $D$ denote the coboundary operator.

1. Prove the discrete topological identity $D^2=0$.
2. Define discrete divergence, curl, and Laplacian using DEC operators.
3. Discuss how mimetic structure improves long-time conservation relative to standard finite differences.

## Problem E. Stable Boundary Layer as a Folded Slow Manifold

Consider

$$
\dot e = F(e,U,\theta),
\qquad
\dot U = \varepsilon G(e,U,\theta),
\qquad
\dot\theta = \varepsilon H(e,U,\theta),
\qquad 0<\varepsilon\ll 1.
$$

1. Define the critical manifold and fold condition.
2. Explain loss of normal hyperbolicity and fast transition behavior.
3. Describe observational diagnostics distinguishing single-fold collapse from two-fold hysteresis.

---

## Suggested Use

- Use one problem as a capstone extension or oral-exam prompt.
- Require both formal derivation and physical interpretation.
- Encourage one computational validation plot for Problems D or E.
