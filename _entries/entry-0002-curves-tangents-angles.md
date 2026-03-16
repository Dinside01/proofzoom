---

layout: entry

title: "Curves, Tangents, and Angles in the Complex Plane"

entry_id: entry-0002
primary_area: complex-analysis
primary_subarea: curves

abstract: "This entry develops the geometric meaning of tangent direction for complex-valued curves, explains how angles between curves may be expressed through arguments of complex numbers, and shows how this leads naturally to conformality. Particular attention is given to the condition $z'(t_0)\\neq 0$, whose meaning in the complex setting is subtler than in the real case."

difficulty: UG-Upper

status: published

published: 2026-03-14

updated:

pdf: /assets/pdfs/entry-0002-curves-tangents-angles.pdf

---

# 1. Overview

A complex-valued curve carries both magnitude and direction at every point. The derivative of such a curve, when nonzero, gives a precise first-order direction of motion. This makes it possible to define tangent rays, angles between curves, and ultimately conformality in a natural geometric way.

The central idea is simple: in the complex plane, a nonzero complex number represents a direction, and the angle from one direction to another is measured by the argument of their ratio.

# 2. Key Idea

If two nonzero complex numbers $v$ and $w$ represent directions, then

the angle from $v$ to $w$ is

$$
\theta = \operatorname{Arg}\!\left(\frac{w}{v}\right).
$$

This identity will allow us to pass from the geometry of tangent directions to a clean formula for the angle between two curves. The crucial hypothesis is that the tangent directions themselves be well defined, which is why the condition $z'(t_0)\neq 0$ plays such an important role.

# 3. Mathematical Formulation

Let $z(t)$ be a complex-valued curve defined on an interval of real numbers, and let

$$
z_0 = z(t_0).
$$

To understand the direction of the curve at $z_0$, consider nearby points

$$
z(t_0-h), \quad z(t_0+h).
$$

The line through these points is a secant line, and its direction is represented by the complex number

$$
z(t_0+h)-z(t_0-h).
$$

As $h\to 0$, these secant directions approach a limiting direction when the derivative exists and is nonzero. This limiting direction is the tangent direction.

To describe lines in the complex plane, it is convenient to use direction vectors. If $a,b\in \mathbb{C}$ with $a\neq b$, then the line through $a$ in the direction $b-a$ may be written parametrically as

$$
z(t)=a+(b-a)t, \qquad t\in \mathbb{R}.
$$

Thus the complex number $b-a$ represents the direction of the line.

Because complex numbers encode direction through argument, the angle between two nonzero directions $v$ and $w$ is

$$
\theta = \operatorname{Arg}\!\left(\frac{w}{v}\right).
$$

Indeed,

$$
\theta = \operatorname{Arg}\!\left(\frac{w}{v}\right)
      = \operatorname{Arg}(w) - \operatorname{Arg}(v).
$$

so the quotient records the rotation needed to move from the direction of $v$ to the direction of $w$, measured as the principal (smallest) rotation between them.

<div class="entry-note">
<strong>Figure 1 (diagram omitted in the web version).</strong>
The diagram shows a smooth complex curve $z(t)$ in the complex plane with three nearby points
$z(t_0-h)$, $z_0=z(t_0)$, and $z(t_0+h)$.
The secant segments illustrate the difference quotients
$(z(t_0+h)-z_0)/h$ and $(z_0-z(t_0-h))/h$, which approach the
tangent direction at $z_0$ as $h \to 0$.
</div>

<div class="pdf-diagram-note">
Illustrative diagrams are available in the <a href="/assets/pdfs/entry-0002-curves-tangents-angles.pdf">PDF version of this entry</a>.
</div>

# 4. Tangent to a Curve

Let

$$
C: z(t), \qquad \alpha \le t \le \beta,
$$

be a curve, let $t_0\in (\alpha,\beta)$, and suppose $z'(t_0)$ exists and $z'(t_0)\neq 0$. Let

$$
z_0 = z(t_0).
$$

For $h>0$, consider the ray from $z_0$ through the nearby point $z(t_0+h)$:

$$
R(z_0,z(t_0+h))
=
\left\{
z : z = z_0 + s\,\frac{z(t_0+h)-z_0}{h}, \ s\ge 0
\right\}.
$$

Since

$$
\lim_{h\to 0^+}\frac{z(t_0+h)-z_0}{h}=z'(t_0)\neq 0,
$$

this ray approaches the ray

$$
T(z_0)=\{z: z=z_0+s\,z'(t_0), \ s\ge 0\}.
$$

as $h\to 0^+$.

Similarly, the backward secant ray determined by $z(t_0-h)$ approaches the opposite ray. We call $T(z_0)$ the tangent ray, since its direction agrees with the direction of travel of the curve.

<div class="entry-note">
<strong>Figure 2 (diagram omitted in the web version).</strong>
The diagram illustrates the geometric interpretation of the derivative
of the curve $z(t)$ at the point $z_0=z(t_0)$.
As $z(t_0+h)$ approaches $z_0$, the direction of the secant line
approaches the tangent direction determined by $z'(t_0)$.
</div>

<div class="pdf-diagram-note">
Illustrative diagrams are available in the <a href="/assets/pdfs/entry-0002-curves-tangents-angles.pdf">PDF version of this entry</a>.
</div>

Thus a curve with $z'(t_0)\neq 0$ possesses a well-defined local first-order direction.

**Remark 4.1.** A tangent may still exist at a point where $z'(t_0)=0$, but then it is determined by higher-order behavior rather than by the first derivative.

# 5. Invariance under Regular Reparametrization

The tangent direction determined by $z'(t_0)$ is intrinsic to the geometric curve and does not depend on the particular parameter used to describe it.

Indeed, a curve parametrized by $t$ may be described using another parameter $\tau$ by writing

$$
\tau = \phi(t),
$$

where $\phi$ is a differentiable function with nonzero derivative. Such a change of parameter is called a regular reparametrization. Since $\phi'(t)\neq 0$, the function $\phi$ is strictly monotone near $t_0$ and so nearby values of $\tau$ correspond to unique nearby values of $t$. Thus the same points of the curve are traced, but at a different rate of traversal. That is, geometrically, reparametrization merely changes the speed at which the curve is traversed, without altering the curve itself.

**Theorem 5.1.** The nonvanishing of $z'(t_0)$ is preserved under regular reparametrizations of the curve.

**Proof.** Let $\tau=\phi(t)$ be a $C^1$ change of parameter with $\phi'(t_0)\neq 0$, and let $\tau_0=\phi(t_0)$. Define the reparametrized curve by

$$
\widetilde z(\tau)=z(\phi^{-1}(\tau)).
$$

By the chain rule,

$$
\widetilde z'(\tau_0)=z'(t_0)(\phi^{-1})'(\tau_0).
$$

Since $\phi'(t_0)\neq 0$, the inverse function theorem gives

$$
(\phi^{-1})'(\tau_0)=\frac{1}{\phi'(t_0)}.
$$

Hence

$$
\widetilde z'(\tau_0)=\frac{z'(t_0)}{\phi'(t_0)}.
$$

Because $\phi'(t_0)$ is a nonzero real number, $\widetilde z'(\tau_0)$ is a nonzero real scalar multiple of $z'(t_0)$. Therefore

$$
\widetilde z'(\tau_0)\neq 0 \iff z'(t_0)\neq 0.
$$

$\square$

**Remark 5.2.** The formula

$$
\widetilde z'(\tau_0)=\frac{z'(t_0)}{\phi'(t_0)}
$$

shows that the derivative under a regular reparametrization differs from the original derivative only by multiplication by a nonzero real number. Such a real scalar multiple changes the magnitude of the vector but not its direction. Consequently the tangent direction of the curve is unchanged by a regular reparametrization.

# 6. Angle Between Curves

Let $C_1$ and $C_2$ be oriented curves intersecting at a point $z_0$. Suppose they admit parametrizations

$$
z_1(t), \quad z_2(t)
$$

such that

$$
z_1(t_0)=z_2(t_0)=z_0
$$

and

$$
z_1'(t_0)\neq 0, \qquad z_2'(t_0)\neq 0.
$$

Then each curve has a well-defined tangent ray at $z_0$.

**Definition 6.1.** The angle from $C_1$ to $C_2$ at $z_0$ is the oriented angle from the tangent ray of $C_1$ to the tangent ray of $C_2$.

Because the tangent directions are represented by the nonzero complex numbers

$$
z_1'(t_0), \quad z_2'(t_0),
$$

the angle between the curves is

$$
\angle(C_1,C_2)=\operatorname{Arg}(z_2'(t_0))-\operatorname{Arg}(z_1'(t_0)).
$$

Using the identity

$$
\operatorname{Arg}\!\left(\frac{w}{v}\right)=\operatorname{Arg}(w)-\operatorname{Arg}(v),
$$

we obtain the fundamental formula

$$
\angle(C_1,C_2)=
\operatorname{Arg}\!\left(\frac{z_2'(t_0)}{z_1'(t_0)}\right).
$$

Thus the angle between curves is determined entirely by the ratio of their tangent directions.

# 7. Conformality

A mapping is conformal if it preserves angles between intersecting curves.

Let $C:z(t)$ be a regular curve and let

$$
z_0=z(t_0).
$$

Suppose $f$ is differentiable at $z_0$ and

$$
f'(z_0)\neq 0.
$$

The image curve

$$
w(t)=f(z(t))
$$

has derivative

$$
w'(t_0)=f'(z_0)z'(t_0).
$$

Thus the tangent direction of the image curve is obtained from the tangent direction of the original curve by multiplication by the complex number $f'(z_0)$.

Multiplication by a nonzero complex number has a simple geometric effect:

* a rotation through the angle $\operatorname{Arg}(f'(z_0))$,
* a uniform scaling by the factor $\lvert f'(z_0)\rvert$.
Now let $C_1$ and $C_2$ be two curves through $z_0$, and let $\Gamma_1,\Gamma_2$ be their images under $f$. Then

$$
\frac{w_2'(t_0)}{w_1'(t_0)}
=
\frac{f'(z_0)z_2'(t_0)}{f'(z_0)z_1'(t_0)}
=
\frac{z_2'(t_0)}{z_1'(t_0)}.
$$

Taking arguments, we obtain

$$
\angle(\Gamma_1,\Gamma_2)=\angle(C_1,C_2).
$$

So the mapping preserves both the magnitude of the angle and the sense of rotation. This is precisely conformality.

**Conceptual conclusion.** Conformality requires two independent nondegeneracy conditions:

$$
z'(t_0)\neq 0, \qquad f'(z_0)\neq 0.
$$

The first guarantees that the curve has a well-defined first-order direction. The second guarantees that the mapping acts locally as a nondegenerate complex scaling. If either fails, the first-order angular structure collapses.

# 8. Local Mapping by an Analytic Function

If $f$ is differentiable at $z_0$, then

$$
\lim_{z\to z_0}
\left\lvert
\frac{f(z)-f(z_0)}{z-z_0}
\right\rvert
=

\lvert f'(z_0)\rvert .
$$

Thus, when $\lvert z-z_0\rvert$ is small,

$\lvert f(z)-f(z_0)\rvert \approx \lvert f'(z_0)\rvert\,\lvert z-z_0\rvert$.

Combined with conformality, this shows that when $f'(z_0)\neq 0$, sufficiently small geometric figures near $z_0$ are mapped to approximately similar figures near $f(z_0)$.

Since

$$
w'(t_0)=f'(z_0)z'(t_0),
$$

we also have

$$
\operatorname{Arg}(w'(t_0))=
\operatorname{Arg}(z'(t_0))+\operatorname{Arg}(f'(z_0)).
$$

So locally the mapping acts like:

* a rotation through angle $\operatorname{Arg}(f'(z_0))$,
* followed by a uniform scaling by the factor $\lvert f'(z_0)\rvert$.

Thus an analytic function with nonzero derivative behaves locally like the linear map

$$
w=az, \qquad a=f'(z_0),
$$

except that this description is only local rather than global.

# 9. Geometric Meaning of the $z'(t_0)\neq 0$ Condition

The requirement

$$
z'(t_0)\neq 0
$$

ensures that the path possesses a well-defined first-order direction at $t_0$.

Writing

$$
z(t)=x(t)+iy(t),
$$

we have

$$
z'(t_0)=x'(t_0)+iy'(t_0).
$$

When $z'(t_0)\neq 0$, the first-order expansion

$$
z(t_0+h)=z(t_0)+h\,z'(t_0)+o(h)
$$

shows that, to first order, the curve near $t_0$ is a straight segment in the direction $z'(t_0)$. This direction determines the tangent line, the limiting direction of secants, and the local angle structure required for conformality.

### What if $z'(t_0)=0$?

If

$$
z'(t_0)=0,
$$

then both components vanish:

$$
x'(t_0)=0, \qquad y'(t_0)=0.
$$

The first-order term disappears:

$$
z(t_0+h)=z(t_0)+o(h).
$$

Thus the curve has no first-order direction at $t_0$; the point becomes geometrically degenerate. This is stronger than what happens in elementary real calculus. For a real graph $y=f(x)$, the condition

$$
f'(x_0)=0
$$

still gives a horizontal tangent. But for a complex curve,

$$
z'(t_0)=0
$$

means that the first-order directional structure itself is absent.

### Higher-order behavior

Let $m\ge 2$ be the smallest index such that

$$
z^{(m)}(t_0)\neq 0.
$$

Then

$$
z(t_0+h)=z(t_0)+\frac{h^m}{m!}z^{(m)}(t_0)+o(h^m).
$$

The local geometry is then controlled by this higher-order term. If $m$ is odd, the curve crosses its limiting direction; if $m$ is even, the curve touches that direction and turns back. In either case, the first-order direction is absent.

**Example 9.1 (Loss of first-order direction).** Consider the curve

$$
z(t)=t^2+it^3.
$$

Then

$$
z'(t)=2t+3it^2,
$$

so $z'(0)=0$.

Writing

$$
x(t)=t^2, \qquad y(t)=t^3,
$$

we obtain

$$
y^2=x^3,
$$

which is a semicubical cusp.

The point $t=0$ is therefore not governed by a nonzero first-order direction. This example illustrates that the condition $z'(t_0)\neq 0$ is not merely technical; it guarantees the existence of the geometric structure required to define tangent directions and angles.

**Remark 9.2 (Comparison with real curves).** It is instructive to compare this behavior with the case of real functions. If a real function $y=f(x)$ satisfies $f'(x_0)=0$, the graph still possesses a well-defined tangent line at $x_0$, namely a horizontal tangent. Thus the first-order direction of the curve is not lost.

In contrast, for a complex curve $z(t)$ the condition $z'(t_0)=0$ eliminates the entire first-order term in the expansion

$$
z(t_0+h)=z(t_0)+h\,z'(t_0)+o(h).
$$

The curve therefore loses its first-order directional structure altogether, and its local geometry is governed by higher-order terms. This distinction explains why the condition $z'(t_0)\neq 0$ is essential when defining angles between complex curves.

# 10. Functions with Nonzero Derivative

We have seen that a function with nonzero derivative at a point is conformal on regular curves passing through that point.

**Theorem 10.1.** Let $f$ be a complex function continuous in a neighborhood of $z(t_0)$, and let

$$
z:[\alpha,\beta]\to \mathbb{C}
$$

be a $C^1$ regular curve. Then $f$ is conformal at the point $z(t_0)$ along the curve if and only if

$$
f'(z(t_0))\neq 0 \qquad \text{and} \qquad z'(t_0)\neq 0.
$$

**Proof.** Assume first that

$$
f'(z(t_0))\neq 0 \qquad \text{and} \qquad z'(t_0)\neq 0.
$$

Since the curve is regular at $t_0$, it possesses a well-defined first-order direction given by $z'(t_0)$. The differentiability of $f$ at $z(t_0)$ yields the expansion

$$
f(z(t_0+h))
=
f(z(t_0))
+
f'(z(t_0))(z(t_0+h)-z(t_0))
+
o(\lvert z(t_0+h)-z(t_0)\rvert).
$$

Thus, to first order, $f$ acts as multiplication by the nonzero complex number $f'(z(t_0))$, which preserves angles and orientation. Hence $f$ is conformal at $z(t_0)$ along the curve.

Conversely, suppose $f$ is conformal at $z(t_0)$ along the curve. If $z'(t_0)=0$, then the curve loses its first-order direction and secant directions need not converge uniquely, so conformality cannot hold. Thus

$$
z'(t_0)\neq 0.
$$

Similarly, if

$$
f'(z(t_0))=0,
$$

then the first-order term in the local expansion of $f$ vanishes, and $f$ locally collapses first-order directional information. Hence

$$
f'(z(t_0))\neq 0.
$$

Therefore both conditions are necessary. $\square$

**Remark 10.2 (Critical points).** If $f$ is analytic and

$$
f'(z_0)=0,
$$

then $f$ is not conformal at $z_0$. In that case the first-order term vanishes, and the behavior of $f$ is governed by the first nonzero higher derivative. If $m\ge 2$ is the smallest integer such that

$$
f^{(m)}(z_0)\neq 0,
$$

then

$$
f(z)=f(z_0)+\frac{f^{(m)}(z_0)}{m!}(z-z_0)^m+o(\lvert z-z_0\rvert ^m).
$$

Geometrically, the mapping behaves locally like

$$
z\mapsto z^m,
$$

so directions are multiplied $m$-fold and angles are not preserved in the first-order conformal sense. Such a point $z_0$ is called a critical point (or branch point when $m\ge 2$).

**Theorem 10.3 (Local inverse).** An analytic function $f$ has a local inverse at $z_0$ if and only if

$$
f'(z_0)\neq 0.
$$

**Remark 10.4 (Derivative of the local inverse).** Let $w_0=f(z_0)$, and suppose $f$ is holomorphic near $z_0$ with $f'(z_0)\neq 0$. Then a local inverse $f^{-1}$ exists near $w_0$, and differentiating

$$
f^{-1}(f(z))=z
$$

gives

$$
(f^{-1})'(w_0)f'(z_0)=1.
$$

Hence

$$
(f^{-1})'(w_0)=\frac{1}{f'(z_0)}.
$$

**Remark 10.5 (Geometric interpretation).** From

$$
(f^{-1})'(w_0)=\frac{1}{f'(z_0)}
$$

we may write

$$
\frac{1}{f'(z_0)}
=
\frac{\overline{f'(z_0)}}{\lvert f'(z_0)\rvert^2}.
$$

Thus the derivative of the inverse is a real scalar multiple of the complex conjugate of $f'(z_0)$. Geometrically this means that the inverse mapping reverses the rotation produced by $f'(z_0)$ while scaling by the reciprocal factor $1/\lvert f'(z_0)\rvert$.

# 11. Globally Conformal Functions

Some basic analytic functions have nonzero derivative everywhere and are therefore conformal on their entire domains.

**Remark 11.1.** Two important examples are:

(a) The exponential function

$$
f(z)=e^z,
$$

for which

$$
f'(z)=e^z\neq 0 \qquad \text{for all } z\in \mathbb{C}.
$$

(b) A Möbius transformation

$$
T(z)=\frac{az+b}{cz+d}, \qquad ad-bc\neq 0,
$$

for which

$$
T'(z)=\frac{ad-bc}{(cz+d)^2}\neq 0
$$

at every point where $T$ is defined.

These examples illustrate the global version of the local principle: a mapping is conformal precisely where its derivative does not vanish.

# 12. Discussion

The geometric content of conformality is first-order. A curve must have a definite first-order direction, and a mapping must act at first order like multiplication by a nonzero complex number. The derivative captures both facts at once.

This is why the condition

$$
z'(t_0)\neq 0
$$

is essential. In the real setting, derivative zero often still leaves a visible tangent direction. In the complex setting, by contrast, the vanishing of the derivative typically means that the first-order geometry itself disappears.

Likewise, the condition

$$
f'(z_0)\neq 0
$$

expresses the fact that the mapping neither collapses directions nor destroys angular structure. Instead, it rotates and scales infinitesimal figures uniformly.

Thus the geometry of angles in the complex plane is encoded by two simple formulas:

$$
\angle(C_1,C_2)
=
\operatorname{Arg}\!\left(\frac{z_2'(t_0)}{z_1'(t_0)}\right).
$$

and

$$
w'(t_0)=f'(z_0)z'(t_0).
$$

Together these formulas explain why analytic functions with nonzero derivative are conformal.

# References

1. L. V. Ahlfors, *Complex Analysis*, 3rd ed., McGraw–Hill, 1979.
2. J. B. Conway, *Functions of One Complex Variable I*, Springer, 1978.
3. T. Needham, *Visual Complex Analysis*, Oxford University Press, 1997.
4. C. Carathéodory, *Theory of Functions of a Complex Variable*, Vol. 1, Chelsea, 1954.
5. E. M. Stein and R. Shakarchi, *Complex Analysis*, Princeton University Press, 2003.

**Cite as: ProofZoom Entry-0002: Curves, Tangents, and Angles in the Complex Plane.**

