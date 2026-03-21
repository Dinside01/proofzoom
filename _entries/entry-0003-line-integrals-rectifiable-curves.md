---
layout: entry
title: "Line Integrals on Rectifiable Curves"
entry_id: entry-0003
primary_area: complex-analysis
primary_subarea: regularity-rectifiability-functions-on-curves
permalink: /entries/entry-0003-line-integrals-rectifiable-curves/

pdf: /assets/pdfs/entry-0003-line-integrals-rectifiable-curves.pdf
abstract: "We define the complex line integral of a continuous function on a rectifiable curve via Riemann-type sums and prove that the definition is well-posed, independent of the choice of tags. The existence of the integral rests on a fundamental balance between analytic control, via uniform continuity, and geometric control, via finite length. We then show that for piecewise C¹ curves this definition agrees with the classical parametrized integral from a to b of f(γ(t))γ'(t) dt, and derive the fundamental estimate that the magnitude of the integral over C is bounded by the maximum of |f(z)| on C times the length of C. Finally, we establish the length formula for piecewise C¹ curves and interpret the line integral as a construction combining analytic, geometric, and algebraic features."
---

## 1. Overview

Line integrals extend the idea of integration from intervals to curves in the complex plane. In the classical setting, this is done using parametrizations and derivatives, but such definitions rely on smoothness of the curve.

The aim of this entry is to define the line integral in a way that remains valid for general rectifiable curves, including those with sharp corners where derivatives may not exist. The construction is based on Riemann-type sums formed from increments along polygonal approximations of the curve.

The key result is that these sums converge for continuous functions on rectifiable curves, and that the limit is independent of the choice of tags. The existence of the integral is governed by two complementary principles:

- the oscillation of $f \circ \gamma$ is controlled by uniform continuity,  
- the total size of increments is controlled by the finite length of the curve.

Together, these ensure that different approximations produce nearly the same sum.

We then show that in the piecewise $C^1$ case, this definition agrees with the classical parametrized integral, thereby reconciling the general theory with familiar formulas. The length of a curve emerges naturally as the geometric quantity underlying both the definition and its estimates.

Finally, we interpret the line integral as a construction that unifies analytic, geometric, and algebraic features, and we indicate its connection with path independence and potential functions. These ideas form the conceptual bridge to the fundamental results of complex analysis.

---

## 2. Introduction

### 2.1 Sharp Corners

Let $f$ be a function and let $x_0$ be a point in its domain. The graph of $f$ is said to have a sharp corner at $x_0$ if the left-hand and right-hand derivatives at $x_0$ exist but are not equal:

$$
\lim_{x \to x_0^-} \frac{f(x) - f(x_0)}{x - x_0}
\ne
\lim_{x \to x_0^+} \frac{f(x) - f(x_0)}{x - x_0}.
$$

At such a point, there is no single tangent line and the graph changes direction abruptly.

---

### 2.2 $C^0$ and $C^1$

- A function $f$ is $C^0$ if it is continuous. The graph has no breaks, but sharp corners are allowed.  
- A function $f$ is $C^1$ if $f'$ exists everywhere and is continuous. The graph of $f$ has no sharp corners; slopes change smoothly.

---

### 2.3 $C^k$ Smoothness

A function $f$ is said to be $C^k$ if its $k$-th derivative exists and is continuous.

Geometrically, this means:

A function $f$ is in $C^k$ if and only if the graph of its $(k-1)$-st derivative has no sharp corners (equivalently, no jump discontinuities).

Each increase in smoothness removes sharp corners one derivative level higher.

---

### 2.4 Takeaway

- Continuity prevents breaks in the graph.  
- Differentiability prevents sharp corners.  
- Higher smoothness prevents sharp corners in higher-order derivatives.

---

## 3. Existence of Line Integral

We approximate the curve $\gamma$ by polygonal segments and replace the differential $dz$ by $\Delta z$. The central difficulty is that the curve may not be smooth, so no derivative $\gamma'(t)$ is available. The key observation is that two independent mechanisms govern the sums:

- the oscillation of $f \circ \gamma$ is controlled by uniform continuity,  
- the total size of increments is controlled by the finite length of the curve.

Together, these ensure that different approximations produce nearly the same sum.

---

### Theorem 3.1 (Existence of $\int_C f(z)\,dz$)

Let $\gamma : [a,b] \to \mathbb{C}$ be continuous and rectifiable with length $L(\gamma) < \infty$, and let $f : \gamma([a,b]) \to \mathbb{C}$ be continuous.

For a partition $P : a = t_0 < \cdots < t_n = b$ and tags $\xi_k \in [t_{k-1}, t_k]$, set

$$
S(P,\xi)
:=
\sum_{k=1}^n
f(\gamma(\xi_k))
\big(
\gamma(t_k) - \gamma(t_{k-1})
\big).
$$

Then $S(P,\xi)$ converges to a limit as $\|P\| \to 0$, independent of the choice of tags. This limit is denoted
$$
\int_C f(z)\,dz.
$$

---

### Proof

Since $f \circ \gamma$ is continuous on the compact interval $[a,b]$, it is uniformly continuous.

Fix $\varepsilon > 0$ and choose $\delta > 0$ such that

$$
|t - s| < \delta
\;\Rightarrow\;
|f(\gamma(t)) - f(\gamma(s))| < \frac{\varepsilon}{L(\gamma)}.
$$

***

Let $P$ be a partition with $\|P\| < \delta$ and let $\xi, \eta$ be two choices of tags. Then for each $k$ we have

$$
|\xi_k - \eta_k|
\le
t_k - t_{k-1}
<
\delta,
$$

hence

$$
|f(\gamma(\xi_k)) - f(\gamma(\eta_k))|
<
\frac{\varepsilon}{L(\gamma)}.
$$

***

Therefore,

$$
|S(P,\xi) - S(P,\eta)|
\le
\sum_{k=1}^n
|f(\gamma(\xi_k)) - f(\gamma(\eta_k))|
\,|\gamma(t_k) - \gamma(t_{k-1})|.
$$

Thus,

$$
|S(P,\xi) - S(P,\eta)|
<
\frac{\varepsilon}{L(\gamma)}
\sum_{k=1}^n
|\gamma(t_k) - \gamma(t_{k-1})|.
$$

By definition of length,

$$
\sum_{k=1}^n
|\gamma(t_k) - \gamma(t_{k-1})|
\le
L(\gamma),
$$

so

$$
|S(P,\xi) - S(P,\eta)| < \varepsilon.
$$

***

Now let $(P,\xi)$ and $(Q,\eta)$ be tagged partitions with $\|P\|, \|Q\| < \delta$, and let

$$
R : a = r_0 < r_1 < \cdots < r_m = b
$$

be a common refinement of $P$ and $Q$.

For each subinterval of $R$ contained in a subinterval of $P$, choose a tag as follows:

$$
[r_{j-1}, r_j] \subset [t_{k-1}, t_k]
\qquad\Longrightarrow\qquad
\tilde{\xi}_j \in [r_{j-1}, r_j].
$$

Similarly, for each subinterval of $R$ contained in a subinterval of $Q$, choose a tag as follows:

$$
[r_{j-1}, r_j] \subset [s_{\ell-1}, s_\ell]
\qquad\Longrightarrow\qquad
\tilde{\eta}_j \in [r_{j-1}, r_j].
$$

Then $(R,\tilde{\xi})$ and $(R,\tilde{\eta})$ are honest tagged partitions.

Moreover,

$$
[r_{j-1}, r_j] \subset [t_{k-1}, t_k]
\qquad\Longrightarrow\qquad
\tilde{\xi}_j,\ \xi_k \in [t_{k-1}, t_k],
$$

and therefore

$$
|\tilde{\xi}_j-\xi_k| \le t_k-t_{k-1} < \delta.
$$
 Since $f \circ \gamma$ is uniformly continuous, it follows that

$$
|f(\gamma(\tilde{\xi}_j)) - f(\gamma(\xi_k))|
<
\frac{\varepsilon}{L(\gamma)}.
$$

***

Writing each curve increment additively,

$$
\gamma(t_k) - \gamma(t_{k-1})
=
\sum_{j \in J_k}
\big(
\gamma(r_j) - \gamma(r_{j-1})
\big),
$$

where $J_k$ indexes those refined subintervals $[r_{j-1}, r_j] \subset [t_{k-1}, t_k]$, we obtain

$$
\begin{aligned}
|S(P,\xi) - S(R,\tilde{\xi})|
&=
\left|
\sum_{k=1}^n
f(\gamma(\xi_k))
\sum_{j \in J_k}
\big(
\gamma(r_j) - \gamma(r_{j-1})
\big)
-
\sum_{j=1}^m
f(\gamma(\tilde{\xi}_j))
\big(
\gamma(r_j) - \gamma(r_{j-1})
\big)
\right| \\
&\le
\sum_{j=1}^m
\left|
f(\gamma(\xi_{k(j)})) - f(\gamma(\tilde{\xi}_j))
\right|
\,|\gamma(r_j) - \gamma(r_{j-1})| \\
&<
\frac{\varepsilon}{L(\gamma)}
\sum_{j=1}^m
|\gamma(r_j) - \gamma(r_{j-1})| \\
&\le \varepsilon,
\end{aligned}
$$

where $k(j)$ denotes the index such that $[r_{j-1}, r_j] \subset [t_{k(j)-1}, t_{k(j)}]$.

***

An identical argument gives

$$
|S(Q,\eta) - S(R,\tilde{\eta})| < \varepsilon.
$$

***

Since $\|R\| < \delta$, the earlier estimate yields

$$
|S(R,\tilde{\xi}) - S(R,\tilde{\eta})| < \varepsilon.
$$

***

Finally, by the triangle inequality,

$$
\begin{aligned}
|S(P,\xi) - S(Q,\eta)|
&\le
|S(P,\xi) - S(R,\tilde{\xi})|
+
|S(R,\tilde{\xi}) - S(R,\tilde{\eta})|
+
|S(R,\tilde{\eta}) - S(Q,\eta)| \\
&< 3\varepsilon.
\end{aligned}
$$

***

This establishes the Cauchy criterion. Hence $S(P,\xi)$ converges as $\|P\| \to 0$ to a limit independent of tags; define this limit to be

$$
\int_C f(z)\,dz.
$$

$\square$

## 4. Smooth Case: Classical Formula

When the curve is smooth, increments satisfy

$$
\gamma(t_k) - \gamma(t_{k-1})
\approx
\gamma'(\xi_k)(t_k - t_{k-1}).
$$

This shows that the geometric increments along the curve are governed by the derivative, so the Riemann-sum definition collapses to an ordinary integral.

---

### Theorem 4.1 (Complex line integral for piecewise $C^1$ curves)

Let $\gamma : [a,b] \to \mathbb{C}$ be piecewise $C^1$ and let $C = \gamma([a,b])$.

If $f : C \to \mathbb{C}$ is continuous, then $\int_C f(z)\,dz$ exists and

$$
\int_C f(z)\,dz
=
\int_a^b f(\gamma(t)) \gamma'(t)\,dt.
$$

In addition,

$$
\left|
\int_C f(z)\,dz
\right|
\le
\max_{z \in C} |f(z)|\,L(C),
$$

where $L(C)$ is the length of $C$.

---

### Proof

Since $f$ is continuous on $C$ and $\gamma$ is continuous, the composition $f \circ \gamma$ is continuous on $[a,b]$.

On each subinterval where $\gamma$ is $C^1$, the function
$$
t \mapsto f(\gamma(t)) \gamma'(t)
$$
is continuous, hence Riemann integrable.

Thus the (piecewise) real integral
$$
\int_a^b f(\gamma(t)) \gamma'(t)\,dt
$$
exists.

---

Let $P : a = t_0 < \cdots < t_n = b$ be a partition and choose tags $\xi_k \in [t_{k-1}, t_k]$.

Consider the Riemann sum for the real integral:

$$
R(P,\xi)
:=
\sum_{k=1}^n
f(\gamma(\xi_k)) \gamma'(\xi_k)(t_k - t_{k-1}).
$$

---

For each $k$, by the fundamental theorem of calculus applied to $\gamma$ on $[t_{k-1}, t_k]$,

$$
\gamma(t_k) - \gamma(t_{k-1})
=
\int_{t_{k-1}}^{t_k} \gamma'(t)\,dt.
$$

Hence

$$
\gamma(t_k) - \gamma(t_{k-1})
-
\gamma'(\xi_k)(t_k - t_{k-1})
=
\int_{t_{k-1}}^{t_k}
\big(\gamma'(t) - \gamma'(\xi_k)\big)\,dt.
$$

---

Taking moduli gives

$$
\left|
\gamma(t_k) - \gamma(t_{k-1})
-
\gamma'(\xi_k)(t_k - t_{k-1})
\right|
\le
\int_{t_{k-1}}^{t_k}
|\gamma'(t) - \gamma'(\xi_k)|\,dt.
$$

---

Because $\gamma'$ is continuous on each smooth subinterval, it is uniformly continuous there. Thus, given $\varepsilon > 0$, we may refine $P$ so that

$$
|\gamma'(t) - \gamma'(\xi_k)| < \varepsilon
\quad \text{for all } t \in [t_{k-1}, t_k].
$$

Hence

$$
\left|
\gamma(t_k) - \gamma(t_{k-1})
-
\gamma'(\xi_k)(t_k - t_{k-1})
\right|
\le
\varepsilon (t_k - t_{k-1}).
$$

---

Multiplying by $\lvert f(\gamma(\xi_k))\rvert $ and summing over $k$ shows that

$$
\sum_{k=1}^n
f(\gamma(\xi_k))
\big(
\gamma(t_k) - \gamma(t_{k-1})
\big)
-
\sum_{k=1}^n
f(\gamma(\xi_k)) \gamma'(\xi_k)(t_k - t_{k-1})
\to 0
\quad \text{as } \|P\| \to 0.
$$

---

But the second sum is exactly the Riemann sum $R(P,\xi)$ for the real integral
$$
\int_a^b f(\gamma(t)) \gamma'(t)\,dt,
$$
so it converges to that integral as $\|P\| \to 0$.

Therefore the first sum (the defining sum for $\int_C f(z)\,dz$) converges to the same limit. This proves

$$
\int_C f(z)\,dz
=
\int_a^b f(\gamma(t)) \gamma'(t)\,dt.
$$

---

Finally, using the bound

$$
\left|
\int_a^b f(\gamma(t)) \gamma'(t)\,dt
\right|
\le
\int_a^b |f(\gamma(t))|\,|\gamma'(t)|\,dt
\le
\max_{z \in C} |f(z)|
\int_a^b |\gamma'(t)|\,dt,
$$

we obtain

$$
\left|
\int_C f(z)\,dz
\right|
\le
\max_{z \in C} |f(z)|\,L(C).
$$

$\square$

---

## 5. Length of a Curve

The notion of length is fundamental to the theory of line integrals, since it controls both the definition and the estimates.

---

### Theorem 5.1 (Length of a piecewise $C^1$ curve)

If $\gamma : [a,b] \to \mathbb{C}$ is piecewise $C^1$, then $\gamma$ is rectifiable and

$$
L(\gamma)
=
\int_a^b |\gamma'(t)|\,dt.
$$

---

### Proof

Assume first that $\gamma \in C^1([a,b])$. For any partition $P : a = t_0 < \cdots < t_n = b$ we have, by the fundamental theorem of calculus,

$$
\gamma(t_k) - \gamma(t_{k-1})
=
\int_{t_{k-1}}^{t_k} \gamma'(t)\,dt.
$$

---

Hence by the triangle inequality,

$$
|\gamma(t_k) - \gamma(t_{k-1})|
\le
\int_{t_{k-1}}^{t_k} |\gamma'(t)|\,dt.
$$

Summing over $k$ gives

$$
\sum_{k=1}^n
|\gamma(t_k) - \gamma(t_{k-1})|
\le
\int_a^b |\gamma'(t)|\,dt.
$$

Taking the supremum over all partitions yields

$$
L(\gamma)
\le
\int_a^b |\gamma'(t)|\,dt.
$$

---

For the reverse inequality, fix $\varepsilon > 0$. Since $\gamma'$ is continuous on $[a,b]$, it is uniformly continuous.

Choose $\delta > 0$ such that

$$
|t - s| < \delta
\;\Rightarrow\;
|\gamma'(t) - \gamma'(s)|
<
\frac{\varepsilon}{b - a}.
$$

---

Take a partition $P$ with $\|P\| < \delta$ and choose tags $\xi_k \in [t_{k-1}, t_k]$. Then

$$
\int_{t_{k-1}}^{t_k} \gamma'(t)\,dt
=
\gamma'(\xi_k)(t_k - t_{k-1})
+
\int_{t_{k-1}}^{t_k}
(\gamma'(t) - \gamma'(\xi_k))\,dt.
$$

---

So

$$
|\gamma(t_k) - \gamma(t_{k-1})|
\ge
|\gamma'(\xi_k)|(t_k - t_{k-1})
-
\int_{t_{k-1}}^{t_k}
|\gamma'(t) - \gamma'(\xi_k)|\,dt.
$$

---

By our choice of $\delta$, the integrand satisfies

$$
|\gamma'(t) - \gamma'(\xi_k)|
<
\frac{\varepsilon}{b - a},
$$

so

$$
\int_{t_{k-1}}^{t_k}
|\gamma'(t) - \gamma'(\xi_k)|\,dt
<
\frac{\varepsilon}{b - a}(t_k - t_{k-1}).
$$

---

Therefore

$$
|\gamma(t_k) - \gamma(t_{k-1})|
\ge
\left(
|\gamma'(\xi_k)| - \frac{\varepsilon}{b - a}
\right)
(t_k - t_{k-1}).
$$

---

Summing gives

$$
\sum_{k=1}^n
|\gamma(t_k) - \gamma(t_{k-1})|
\ge
\sum_{k=1}^n
|\gamma'(\xi_k)|(t_k - t_{k-1})
-
\varepsilon.
$$

---

The sum
$$
\sum_{k=1}^n
|\gamma'(\xi_k)|(t_k - t_{k-1})
$$
is a Riemann sum for
$$
\int_a^b |\gamma'(t)|\,dt,
$$
hence for sufficiently fine $P$ it is within $\varepsilon$ of the integral.

Thus for fine enough partitions,

$$
\sum_{k=1}^n
|\gamma(t_k) - \gamma(t_{k-1})|
\ge
\int_a^b |\gamma'(t)|\,dt - 2\varepsilon.
$$

---

Taking the supremum over partitions yields

$$
L(\gamma)
\ge
\int_a^b |\gamma'(t)|\,dt.
$$

Combining with the earlier inequality gives equality.

If $\gamma$ is piecewise $C^1$, apply the $C^1$ argument on each smooth subinterval and add the lengths.

$\square$

---

## 6. Interpretation and Structural Consequences

### 6.1 What the Line Integral Really Is

We defined the line integral
$$
\int_C f(z)\,dz
$$
through Riemann-type sums
$$
\sum f(z_k)\,\Delta z_k,
$$
without assuming that the curve is smooth.

The results established in this entry show that:

- the definition is intrinsic to the curve and does not depend on the choice of tags,  
- in the piecewise $C^1$ case it reduces to the familiar integral  
$$
\int_a^b f(\gamma(t)) \gamma'(t)\,dt,
$$
- the geometry of the curve enters through its length, which controls the size of the integral through the estimate  
$$
\left|
\int_C f(z)\,dz
\right|
\le
\max_{z \in C} |f(z)|\,L(C).
$$

---

Thus the line integral combines three features:

- analysis, through limits and uniform continuity,  
- geometry, through finite length,  
- algebra, through complex multiplication.  

---

### 6.2 Bridge: Path Independence and Potentials

A natural question now arises:

When does a line integral depend only on the endpoints of the curve?

---

### Theorem 6.1 (Path independence criterion)

Let $\Omega \subset \mathbb{C} \simeq \mathbb{R}^2$, and consider the line integral
$$
\int_\gamma (p\,dx + q\,dy),
$$
where $p$ and $q$ are continuous functions on $\Omega$.

Then the integral depends only on the endpoints of $\gamma$ if and only if there exists a function $U : \Omega \to \mathbb{R}$ such that

$$
\frac{\partial U}{\partial x} = p,
\qquad
\frac{\partial U}{\partial y} = q.
$$

---

In that case,
$$
\int_\gamma (p\,dx + q\,dy)
=
U(\text{endpoint}) - U(\text{starting point}).
$$

---

Thus line integrals are not merely geometric constructions; they also detect whether a field possesses an underlying scalar potential.

In complex analysis this idea becomes central. Expressions of the form $f(z)\,dz$ encode two real components $p\,dx + q\,dy$, and the question of path independence leads naturally to exactness, holomorphicity, and ultimately to Cauchy’s theorem.

---

## References

- A.-L. Cauchy, *Cours d’Analyse de l’École Royale Polytechnique*, 1821  
- C. Jordan, *Cours d’Analyse*, 1882  
- L. V. Ahlfors, *Complex Analysis*, 3rd ed., McGraw–Hill, 1979  
- J. B. Conway, *Functions of One Complex Variable I*, 2nd ed., Springer, 1978  
- T. M. Apostol, *Mathematical Analysis*, 2nd ed., Addison–Wesley, 1974  

---

**Cite as:**  
ProofZoom Entry-0003 — *Line Integrals on Rectifiable Curves*, ProofZoom (2026)
