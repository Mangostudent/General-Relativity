# 2. Introduction to Tensors
**Date:** 2020-08-26
**Source:** MIT 8.962 General Relativity (MIT OpenCourseWare), Prof. Scott Hughes — [Lecture 2 Recording](https://www.youtube.com/watch?v=TiHHz3sKDbY)

## Context
This lecture bridges basic 4-vectors to tensor calculus in spacetime. It investigates the inverse transformation properties of basis vectors, introduces the Minkowski metric tensor $\eta_{\alpha\beta}$ as an inner product, defines essential kinematic 4-vectors ($U^\alpha, P^\alpha, A^\alpha$), and formalizes tensors as multilinear maps from vectors to invariant scalars.

## Prerequisites
* **Spacetime as a Manifold of Events:** Spacetime is modeled as an event manifold where events exist independently of observer coordinates (Lecture 1).
* **Lorentz Boost Transformations:** Coordinate changes between inertial frames $O$ and $\bar{O}$ mediated by $\Lambda^{\bar{\alpha}}{}_\beta$ (Lecture 1).
* **Einstein Summation Convention:** Contraction over repeated upstairs/downstairs indices.

## Definitions
* **Basis Vectors and Vector Expansion** ($\{\vec{e}_\alpha\}$): A set of four linearly independent vectors defining a frame's coordinate directions such that any geometric vector $\vec{A}$ is written $\vec{A} = A^\alpha \vec{e}_\alpha$.
* **Coordinate Basis Vectors**: Basis vectors defined via coordinate differentials $d\vec{x} = dx^\alpha \vec{e}_\alpha$. In curvilinear systems (e.g., spherical), coordinate basis vectors do not necessarily have unit length or mutual orthogonality.
* **Minkowski Metric Tensor** ($\eta_{\alpha\beta}$): A symmetric rank-$(0, 2)$ tensor defining the inner product of Cartesian coordinate basis vectors in flat spacetime ($c = 1$):
  $$\eta_{\alpha\beta} \equiv \vec{e}_\alpha \cdot \vec{e}_\beta = \operatorname{diag}(-1, 1, 1, 1)$$
* **Spacetime Vector Norm Classification**:
  * **Timelike:** $\vec{A} \cdot \vec{A} < 0$
  * **Spacelike:** $\vec{A} \cdot \vec{A} > 0$
  * **Null / Lightlike:** $\vec{A} \cdot \vec{A} = 0$
* **4-Velocity** ($U^\alpha$): The tangent vector describing the rate of change of spacetime position with respect to proper time $\tau$:
  $$U^\alpha \equiv \frac{dx^\alpha}{d\tau} = (\gamma, \gamma \vec{v}), \quad \gamma = \frac{1}{\sqrt{1 - |\vec{v}|^2}}$$
* **4-Momentum** ($P^\alpha$): The product of rest mass $m$ and 4-velocity:
  $$P^\alpha \equiv m U^\alpha = (E, \vec{p})$$
* **4-Acceleration** ($A^\alpha$): The proper-time derivative of the 4-velocity:
  $$A^\alpha \equiv \frac{dU^\alpha}{d\tau}$$
* **Tensor of Type $(0, n)$**: A multilinear mapping that takes $n$ four-vectors as input arguments and outputs a real, Lorentz-invariant scalar:
  $$T: \underbrace{V \times V \times \dots \times V}_{n \text{ arguments}} \to \mathbb{R}$$

## Key Results
* **Dual Transformation of Basis Vectors:** For the geometric vector $\vec{A} = A^\alpha \vec{e}_\alpha$ to remain invariant under a change of frame, basis vectors must transform via the inverse Lorentz transformation:
  $$\vec{e}_\alpha = \Lambda^{\bar{\beta}}{}_\alpha \vec{e}_{\bar{\beta}} \iff \vec{e}_{\bar{\beta}} = \Lambda^\alpha{}_{\bar{\beta}} \vec{e}_\alpha$$
  * *Sketch:* Equate $\vec{A} = A^{\bar{\beta}} \vec{e}_{\bar{\beta}} = (\Lambda^{\bar{\beta}}{}_\alpha A^\alpha) \vec{e}_{\bar{\beta}}$ to $A^\alpha \vec{e}_\alpha$ and factor out the arbitrary component $A^\alpha$.
* **Fundamental Invariant Norm of 4-Velocity:** For any massive particle:
  $$\vec{U} \cdot \vec{U} = \eta_{\alpha\beta} U^\alpha U^\beta = -1$$
  * *Sketch:* Evaluated in the particle's rest frame where $U^\alpha \doteq (1, 0, 0, 0)$.
* **Relativistic Energy-Momentum Invariant:**
  $$\vec{P} \cdot \vec{P} = -m^2 = -E^2 + |\vec{p}|^2 \implies E^2 = |\vec{p}|^2 + m^2$$
* **Observer-Measured Energy as an Invariant Projection:** The energy $E_{\text{obs}}$ of a particle with 4-momentum $\vec{P}$ measured by an observer with 4-velocity $\vec{U}_{\text{obs}}$ is:
  $$E_{\text{obs}} = -\vec{P} \cdot \vec{U}_{\text{obs}} = -\eta_{\alpha\beta} P^\alpha U_{\text{obs}}^\beta$$
  * *Sketch:* In the observer's rest frame, $\vec{U}_{\text{obs}} \doteq (1, \vec{0})$ and $\vec{P} \doteq (E_{\text{obs}}, \vec{p}_{\text{obs}})$; taking the negative Minkowski inner product directly yields $E_{\text{obs}}$.
* **Orthogonality of 4-Acceleration and 4-Velocity:**
  $$\vec{A} \cdot \vec{U} = 0$$
  * *Sketch:* Differentiate the constant constraint $\vec{U} \cdot \vec{U} = -1$ with respect to $\tau$: $\frac{d}{d\tau}(\vec{U} \cdot \vec{U}) = 2\vec{U} \cdot \vec{A} = 0$.

## Proof Techniques
* **Privileged Frame Evaluation (Rest-Frame Trick)** [Reusability: High]:
  * *Core Mechanism:* To calculate the invariant scalar contracted from several 4-vectors/tensors, evaluate it in a specially chosen reference frame (such as the rest frame or center-of-momentum frame) where components simplify dramatically. Because the resulting quantity is a Lorentz scalar, that value holds true in all frames without computing explicit Lorentz boost matrices.
  * *Demonstrated in:* Proving $\vec{U} \cdot \vec{U} = -1$ and deriving $E_{\text{obs}} = -\vec{P} \cdot \vec{U}_{\text{obs}}$.
  * *When to use:* Particle collision thresholds, invariant masses, and finding observer-measured physical scalar projections.
* **Metric Contraction for Invariant Inner Products** [Reusability: High]:
  * *Core Mechanism:* Expand geometric vectors in their coordinate basis and express their scalar product via the metric tensor:
    $$\vec{A} \cdot \vec{B} = (A^\alpha \vec{e}_\alpha) \cdot (B^\beta \vec{e}_\beta) = A^\alpha B^\beta (\vec{e}_\alpha \cdot \vec{e}_\beta) = \eta_{\alpha\beta} A^\alpha B^\beta$$
  * *Demonstrated in:* Defining the spacetime interval $\Delta s^2$ and the metric tensor $\eta_{\alpha\beta}$.
  * *When to use:* Generalizing dot products to curved spacetimes and non-Cartesian curvilinear coordinate systems.
* **Differentiation of Invariant Scalar Constraints** [Reusability: Medium]:
  * *Core Mechanism:* Differentiating a fixed scalar norm constraint along a worldline parameter immediately reveals geometric orthogonality conditions for higher derivative vectors.
  * *Demonstrated in:* Differentiating $\vec{U} \cdot \vec{U} = -1$ to show $\vec{A} \cdot \vec{U} = 0$.

## Application
* **Problem:** A cosmic ray proton (rest mass $m$) travels along the $x^1$-axis with energy $E_L$ measured in the laboratory frame. A detector moves along the same axis with speed $v$ relative to the lab. Using invariant 4-vector contractions, find the proton's energy $E_{\text{det}}$ recorded by the detector without applying Lorentz transformation matrices to the component coordinates.

* **Solution:**
  1. **Specify 4-Vectors in the Laboratory Frame ($c = 1$):**
     * Proton 4-momentum: $P^\alpha \doteq (E_L, p_L, 0, 0)$ where $p_L = \sqrt{E_L^2 - m^2}$.
     * Detector 4-velocity: $U_{\text{det}}^\alpha \doteq (\gamma, \gamma v, 0, 0)$ where $\gamma = (1 - v^2)^{-1/2}$.
  2. **Compute the Invariant Contraction:**
     Applying Key Result $E_{\text{det}} = -\vec{P} \cdot \vec{U}_{\text{det}} = -\eta_{\alpha\beta} P^\alpha U_{\text{det}}^\beta$:
     $$\eta_{\alpha\beta} P^\alpha U_{\text{det}}^\beta = -P^0 U_{\text{det}}^0 + P^1 U_{\text{det}}^1 = -E_L \gamma + p_L (\gamma v) = -\gamma(E_L - v p_L)$$
  3. **Evaluate $E_{\text{det}}$:**
     $$E_{\text{det}} = -[-\gamma(E_L - v p_L)] = \gamma(E_L - v p_L) = \frac{E_L - v\sqrt{E_L^2 - m^2}}{\sqrt{1 - v^2}}$$
     The scalar invariant directly recovers the boosted energy measurement.

**Tags:** general-relativity, special-relativity, tensors, four-vectors, four-velocity, minkowski-metric, proper-time, invariant-scalars, scott-hughes
