---
layout: entry
title: "Curves, Tangents, and Angles in the Complex Plane"
entry_id: entry-0002
primary_area: complex-analysis
primary_subarea: curves-and-conformality
abstract: "This entry develops the geometric meaning of tangent direction for complex-valued curves, explains how angles between curves may be expressed through arguments of complex numbers, and shows how this leads naturally to conformality. Particular attention is given to the condition $z'(t_0)\neq 0$, whose meaning in the complex setting is subtler than in the real case."
difficulty: UG-Upper
status: published
published: 2026-03-14
updated:
pdf: /assets/pdfs/entry-0002-curves-tangents-angles.pdf
---

## 1. Overview

A complex-valued curve carries both magnitude and direction at every point.  
The derivative of such a curve, when nonzero, gives a precise first-order direction of motion.  
This makes it possible to define tangent rays, angles between curves, and ultimately conformality in a natural geometric way.

The central idea is simple: in the complex plane, a nonzero complex number represents a direction, and the angle from one direction to another is measured by the argument of their ratio.

## 2. Key Idea

If two nonzero complex numbers \(v\) and \(w\) represent directions, then the angle from \(v\) to \(w\) is

$$
\theta = \operatorname{Arg}\!\left(\frac{w}{v}\right).
$$

This identity allows us to pass from the geometry of tangent directions to a clean formula for the angle between two curves.

## 3. Mathematical Formulation

Let \(z(t)\) be a complex-valued curve defined on an interval of real numbers, and suppose

$$
z'(t_0) \neq 0.
$$

Then the tangent direction at \(z(t_0)\) is given by the complex number \(z'(t_0)\).

If \(z_1(t)\) and \(z_2(t)\) are two curves passing through the same point \(z_0\), with derivatives \(z_1'(t_0)\) and \(z_2'(t_0)\), the angle between the curves is

$$
\angle(C_1,C_2)
=
\operatorname{Arg}\!\left(\frac{z_2'(t_0)}{z_1'(t_0)}\right).
$$