# Handout: Geometric Methods in Geophysical Fluid Dynamics (GFD)

## Bridging Vector Calculus and Differential Forms

Traditional atmospheric science relies heavily on standard vector calculus ($\nabla \cdot$, $\nabla \times$, $\times$). However, on a rotating, spherical planet with complex vertical coordinates, this notation becomes cumbersome. Framing the primitive equations using **Differential Forms** and **Geometric Mechanics** isolates the invariant topology of the fluid from the metric properties of the coordinate system.

This guide translates standard atmospheric concepts into geometric language using the Exterior Derivative ($d$), the Lie Derivative ($\mathcal{L}_{\vec{u}}$), and the Hodge Star operator ($\star$).

---

## 1. The Kinematics: From Vectors to Forms

In standard GFD, we track velocity as a vector field $\vec{u} = (u, v, w)$ and relative vorticity as its curl, $\vec{\omega} = \nabla \times \vec{u}$. In geometric mechanics, we lower an index using the metric tensor to transform the velocity vector field into a **velocity 1-form**, denoted as $u$.

Taking the exterior derivative ($d$) of the velocity 1-form naturally yields the **vorticity 2-form**:

$$\omega = du$$

### Circulation and Stokes' Theorem

When calculating fluid circulation ($\Gamma$), meteorologists integrate the velocity vector along a closed loop. By Stokes' Theorem, this is topologically identical to integrating the vorticity 2-form over the enclosed bounding surface:

$$\Gamma = \oint_{\partial S} u = \int_{S} du = \int_{S} \omega$$

This coordinate-free definition means Kelvin’s Circulation Theorem holds identically regardless of whether you are computing it on a flat Cartesian grid or a distorted cubed-sphere mesh.

---

## 2. Dynamics and Advection: The Lie Derivative

The total or material derivative ($\frac{D}{Dt}$) tracks properties within a moving parcel of air. Geometrically, this tracking is governed by the **Lie Derivative** ($\mathcal{L}_{\vec{u}}$) along the fluid velocity vector field $\vec{u}$.

To compute how any differential form $\alpha$ changes dynamically within the flow, we employ **Cartan's Magic Formula**:

$$\mathcal{L}_{\vec{u}}\alpha = i_{\vec{u}}(d\alpha) + d(i_{\vec{u}}\alpha)$$

Where $i_{\vec{u}}$ is the interior product (contraction) with the velocity field.

### Case A: Thermodynamic Advection (0-forms)

Let $\alpha = T$ (Temperature, a 0-form scalar). Since the exterior derivative of a contracted scalar is zero ($i_{\vec{u}}T = 0$), Cartan's formula simplifies to:

$$\mathcal{L}_{\vec{u}}T = i_{\vec{u}}(dT) = \vec{u} \cdot \nabla T$$

This recovers the standard mathematical definition of horizontal and vertical thermal advection ($u\frac{\partial T}{\partial x} + v\frac{\partial T}{\partial y} + w\frac{\partial T}{\partial z}$).

### Case B: Vorticity Dynamics (2-forms)

When applied to the vorticity 2-form $\omega$, the Lie derivative $\mathcal{L}_{\vec{u}}\omega$ expands to automatically encapsulate **vorticity advection, vortex stretching, and vortex tilting** in a single term, bypassing the need for tedious vector cross-product expansions.

---

## 3. Duality and Rotation: The Hodge Star Operator ($\star$)

The Hodge star operator maps a $k$-form in an $n$-dimensional space to an $(n-k)$-form, establishing a geometric duality. It computes the orthogonal complement of a geometric object scaled by the local volume element.

In a 3D atmosphere ($n=3$):

* **0-forms** (Scalars: $p, T$) $\stackrel{\star}{\longleftrightarrow}$ **3-forms** (Volume densities: $\rho \, dV$)
* **1-forms** (Velocity/Momenta: $u$) $\stackrel{\star}{\longleftrightarrow}$ **2-forms** (Fluxes through surfaces: $\star u$)

### The 2D Hodge Star and Streamfunctions

Many foundational GFD frameworks (e.g., Shallow Water, Quasi-Geostrophic models) isolate horizontal layers where the flow is approximately 2D ($n=2$).

In a 2D plane, applying the Hodge star to a 1-form rotates it by **90 degrees**:

$$\star (u\,dx + v\,dy) = -v\,dx + u\,dy$$

If the horizontal flow is nondivergent ($\nabla \cdot \vec{u}_h = 0$), its volume form is preserved, meaning the flux form is closed: $d(\star u) = 0$. By Poincaré's Lemma, it must be locally exact, establishing the existence of a 0-form scalar **streamfunction ($\psi$)**:

$$\star u = d\psi \implies u = -\star d\psi$$

Expanding $u = -\star d\psi$ in standard Cartesian components directly yields the familiar kinematic definitions:

$$u = -\frac{\partial \psi}{\partial y}, \quad v = \frac{\partial \psi}{\partial x}$$

---

## 4. The Laplacian: Solving the QG Omega and PV Equations

Whether inverting Quasi-Geostrophic Potential Vorticity (QGPV) to solve for winds or evaluating the QG Omega equation for vertical motion, atmospheric models constantly solve elliptic Poisson equations ($\nabla^2 \phi = f$).

In differential forms, the geometric Laplacian is defined via the **Laplace-de Rham operator** ($\Delta$) using the codifferential $\delta = -\star d \star$:

$$\Delta \psi = \delta d \psi = -\star d \star d \psi$$

Breaking down this operation step-by-step demonstrates how the Hodge star facilitates the operation:

1. $d\psi$ converts the scalar 0-form streamfunction into a 1-form (gradient).
2. $\star d\psi$ rotates this gradient by 90 degrees (generating the velocity 1-form).
3. $d(\star d\psi)$ takes the exterior derivative of the velocity, yielding a 2-form (vertical relative vorticity field, $\zeta \, dx \wedge dy$).
4. $-\star (d\star d\psi)$ scales the 2-form back into a scalar 0-form ($\zeta$).

Thus, $-\star d \star d \psi = \zeta$ is the exact, coordinate-free equivalent to $\nabla^2 \psi = \zeta$.

---

## Quick-Reference Notation Dictionary

| Physical Atmospheric Concept | Standard Vector Notation | Differential Forms Equivalent |
| --- | --- | --- |
| **Velocity Vector / 1-form** | $\vec{u} = (u,v,w)$ | $u = u_i dx^i$ |
| **Relative Vorticity** | $\vec{\omega} = \nabla \times \vec{u}$ | $\omega = du$ |
| **Horizontal Divergence** | $\nabla \cdot \vec{u}_h = 0$ | $d(\star u) = 0$ |
| **Material Derivative** | $\frac{D\alpha}{Dt}$ | $\frac{\partial \alpha}{\partial t} + \mathcal{L}_{\vec{u}}\alpha$ |
| **Baroclinic Vector Production** | $\frac{1}{\rho^2}(\nabla \rho \times \nabla p)$ | $d\theta \wedge dp \quad \text{or} \quad dT \wedge ds$ |
| **Laplacian Operations ($\nabla^2 \phi$)** | $\frac{\partial^2 \phi}{\partial x^2} + \frac{\partial^2 \phi}{\partial y^2}$ | $-\star d \star d \phi$ |

---

To fully grasp how **advection** behaves in fluid dynamics, it helps to step away from traditional vector calculus—which relies on coordinate grids—and look at it through the lens of differential geometry.

In atmospheric science and geophysical fluid dynamics (GFD), tracking how a property changes as it is carried by the wind is completely managed by the **Lie derivative ($\mathcal{L}_{\vec{u}}$)** along a velocity vector field $\vec{u}$.

---

### 1. The Core Intuition: "Dragging" Fields

The Lie derivative evaluates how a geometric object (a scalar, a vector field, or a differential form) changes when it is "dragged" or "flowed" along the trajectories of a vector field.

Think of the atmosphere as a moving continuous medium. If you stamp a coordinate grid onto a parcel of air and let the wind blow, that grid will deform, stretch, and rotate. The Lie derivative measures the change of a physical field relative to that *deforming* fluid frame, rather than a fixed frame on Earth.

---

### 2. Cartan's Magic Formula

To compute the Lie derivative of any differential form $\alpha$, we use **Cartan's magic formula**:

$$\mathcal{L}_{\vec{u}}\alpha = i_{\vec{u}}(d\alpha) + d(i_{\vec{u}}\alpha)$$

Where:

* $d$ is the exterior derivative (generalizing grad, curl, and div).
* $i_{\vec{u}}$ is the interior product (or contraction), which inserts the velocity vector $\vec{u}$ into a component of the form.

---

### 3. Case 1: Advection of a Scalar (0-form)

Let's look at a scalar field like temperature, $T$. In differential geometry, a scalar is a **0-form**.

Let's plug a 0-form into Cartan's formula:

1. **First term ($i_{\vec{u}}(dT)$):** The exterior derivative $dT$ is a 1-form (the gradient). Contracting it with the velocity vector field $\vec{u}$ means evaluating the gradient along that vector: $i_{\vec{u}}(dT) = \vec{u} \cdot \nabla T$.
2. **Second term ($d(i_{\vec{u}}T)$):** You cannot contract a 0-form because it has no spatial slots to insert a vector into. Therefore, $i_{\vec{u}}T = 0$, which makes $d(0) = 0$.

Putting it together:


$$\mathcal{L}_{\vec{u}}T = i_{\vec{u}}(dT) = \vec{u} \cdot \nabla T$$

This is exactly the classical **advection term** you see in the atmospheric thermodynamic energy equation. If $\mathcal{L}_{\vec{u}}T > 0$, the wind is bringing a change in temperature to that fluid element.

---

### 4. Case 2: Advection of Vorticity (2-form)

Now consider the relative vorticity 2-form, $\omega = du$. Because vorticity is a 2-form, its interaction with the flow is much richer than a simple scalar. A 2-form describes a flux through an area, and as the fluid moves, that area can stretch or tilt.

Let's apply Cartan's formula to $\omega$:


$$\mathcal{L}_{\vec{u}}\omega = i_{\vec{u}}(d\omega) + d(i_{\vec{u}}\omega)$$

1. **First term ($i_{\vec{u}}(d\omega)$):** Because $\omega = du$, $d\omega = d(du) = 0$ (the exterior derivative of an exterior derivative is always zero). So, this term vanishes completely.
2. **Second term ($d(i_{\vec{u}}\omega)$):** This leaves us with just $d(i_{\vec{u}}\omega)$.

When you expand $d(i_{\vec{u}}\omega)$ using standard vector identities, it automatically unpacks into **three distinct physical processes** that meteorologists care about:

$$\mathcal{L}_{\vec{u}}\omega = \underbrace{(\vec{u} \cdot \nabla)\vec{\omega}}_{\text{Translational Advection}} - \underbrace{(\vec{\omega} \cdot \nabla)\vec{u}}_{\text{Vortex Tilting \& Stretching}} + \underbrace{\vec{\omega}(\nabla \cdot \vec{u})}_{\text{Divergence / Compression}}$$

### Why this is mathematically beautiful:

In traditional vector calculus text books, deriving the vorticity equation requires taking the curl of the Navier-Stokes equations, resulting in a massive algebraic headache of cross-products and vector identities to isolate advection, stretching, and tilting.

In geometric mechanics, **Cartan's magic formula generates all three terms simultaneously and automatically** simply because the Lie derivative natively understands how an area element deforms as it is advected through space.