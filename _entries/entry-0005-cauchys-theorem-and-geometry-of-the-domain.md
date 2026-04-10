---
layout: entry
title: "Cauchy’s Integral Theorem and Geometry of the Domain"
entry_id: entry-0005
primary_area: Complex Analysis
primary_subarea: Cauchy Theory
difficulty: UG-Upper

published: 2026-03-30
updated:

permalink: /entries/entry-0005-cauchys-theorem-and-geometry-of-the-domain/

pdf: /assets/pdfs/entry-0005-cauchys-theorem-and-geometry-of-the-domain.pdf

abstract:  "Cauchy’s theorem asserts that the integral of a holomorphic function around a closed curve vanishes. Beyond this striking phenomenon lies a deeper truth: the theorem reflects a fundamental property of the domain itself. In simply connected regions, holomorphic functions behave as global derivatives, and their integrals detect no circulation. Conversely, any failure of such behavior reveals the presence of a hole. Thus complex integration encodes the topology of the plane."

---

## 1. The phenomenon

A function possessing a complex derivative at every point of its domain is called *holomorphic* (or *analytic*). Let $f$ be holomorphic on a region $D \subset \mathbb{C}$ (that is, a connected open set — equivalently, any two points in $D$ can be joined by a polygonal path lying entirely in $D$). 

In real-variable calculus, the definite integral of a derivative over an interval depends only on the endpoints. In complex analysis, a similar phenomenon occurs — but under subtler conditions.

If a function $f$ admits a primitive $F$ on $D$, then integrals of $f$ along curves depend only on the endpoints. More strikingly, even without assuming a primitive, this path-independence holds for every holomorphic function provided the domain $D$ has no holes (that is, is simply connected).

Equivalently, in such domains, the integral of a holomorphic function around any closed curve vanishes:
$$
\int_\gamma f(z)\,dz = 0.
$$

This is Cauchy’s theorem. Thus Cauchy’s theorem is not only about holomorphic functions, but about the geometry of the domain itself.


## 2. Cauchy’s theorem (Goursat’s proof)

We present a proof that assumes only complex differentiability.

**Theorem.** Let $T$ be a triangle together with its interior, and let $f$ be holomorphic on an open set containing $T$. Then

$$
\int_{\partial T} f(z)\,dz = 0.
$$

**Proof.** Define

$$
I(T) =
\int_{\partial T}
f(z)\,dz.
$$

Divide the triangle into four similar triangles by joining the midpoints of its sides. Then

$$
I(T) = I(T_1) + I(T_2) + I(T_3) + I(T_4),
$$

so one of the subtriangles satisfies

$$
|I(T^{(1)})| \ge \frac{1}{4} |I(T)|.
$$

Repeating this construction produces a nested sequence of triangles

$$
T \supset T^{(1)} \supset T^{(2)} \supset \cdots
$$

with diameters tending to zero. Write

$$
T^{(n)} \subset [a_n, b_n] + i[c_n, d_n],
$$

where $[a_n, b_n]$ is the smallest closed interval containing the real parts of points of $T^{(n)}$, and $[c_n, d_n]$ is the smallest closed interval containing the imaginary parts.

Because $T^{(n+1)} \subset T^{(n)}$, we have

$$
[a_{n+1}, b_{n+1}] \subset [a_n, b_n], \quad [c_{n+1}, d_{n+1}] \subset [c_n, d_n].
$$

Thus the intervals form two nested sequences of closed intervals.

Moreover, since the diameters of the triangles tend to $0$, we also have

$$
b_n - a_n \to 0, \quad d_n - c_n \to 0.
$$

By the Nested Interval Theorem, there exist unique real numbers $x_0$ and $y_0$ such that

$$
\bigcap_{n=0}^{\infty} [a_n, b_n] = \{x_0\}, \quad
\bigcap_{n=0}^{\infty} [c_n, d_n] = \{y_0\}.
$$

Hence

$$
\bigcap_{n=0}^{\infty} T^{(n)} = \{x_0 + i y_0\}.
$$

We denote this unique point by

$$
z_0 = x_0 + i y_0.
$$

(For uniqueness, it is sufficient that the intersection of the compact sets is nonempty; the nonempty set is forced to be a singleton set. For if $w$ is another point in $\bigcap_{n=1}^{\infty} T^{(n)}$, then for every $n$ both $z_0$ and $w$ lie in $T^{(n)}$, so

$$
|z_0 - w| \le \operatorname{diam}(T^{(n)}).
$$

Since $\operatorname{diam}(T^{(n)}) \to 0$, it follows that $\lvert z_0 - w\rvert                                                                                                                 = 0$, hence $w = z_0$. Therefore

$$
\bigcap_{n=1}^{\infty} T^{(n)} = \{z_0\}.
$$

Thus the nested triangles shrink to the single point $z_0$.)

Since $f$ is differentiable at $z_0$,

$$
f(z) = f(z_0) + f'(z_0)(z - z_0) + \varepsilon(z)(z - z_0),
$$

where $\varepsilon(z) \to 0$ as $z \to z_0$.

The constant and linear terms integrate to zero around $\partial T^{(n)}$, so

$$
I(T^{(n)}) =
\int_{\partial T^{(n)}} \varepsilon(z)(z - z_0)\,dz.
$$

We estimate the integral. Define

$$
\delta_n := \sup_{z \in T^{(n)}} |\varepsilon(z)|.
$$

Since $\varepsilon(z) \to 0$ as $z \to z_0$ and the diameters of $T^{(n)}$ tend to $0$, we have $\delta_n \to 0$.

Also, for $z \in T^{(n)}$,

$$
|z - z_0| \le \operatorname{diam}(T^{(n)}).
$$

Hence

$$
|\varepsilon(z)(z - z_0)| \le \delta_n \operatorname{diam}(T^{(n)}).
$$

Therefore,

$$
|I(T^{(n)})| \le \int_{\partial T^{(n)}} |\varepsilon(z)(z - z_0)|\,|dz| \le \delta_n \operatorname{diam}(T^{(n)}) \operatorname{length}(\partial T^{(n)}).
$$

Since the perimeter of a triangle is at most three times its diameter,

$$
\operatorname{length}(\partial T^{(n)}) \le 3 \operatorname{diam}(T^{(n)}).
$$

Thus

$$
|I(T^{(n)})| \le 3 \delta_n (\operatorname{diam}(T^{(n)}))^2.
$$

Because $\operatorname{diam}(T^{(n)}) = 2^{-n} \operatorname{diam}(T)$, it follows that

$$
|I(T^{(n)})| \le C \delta_n 4^{-n},
$$

where $C = 3(\operatorname{diam}(T))^2$.

But also

$$
4^n |I(T^{(n)})| \ge |I(T)|.
$$

Letting $n \to \infty$ forces $I(T) = 0$.

$\square$

**From triangles to rectangles and then to closed curves**

The triangular case immediately implies the theorem for rectangles, since every rectangle can be divided into two triangles by a diagonal. Hence the integral of $f$ around the boundary of any rectangle in the domain is zero.

Now let a region be tiled by finitely many rectangles. Since the integral around each rectangle is zero, the sum of all these boundary integrals is zero. Along every interior edge, the two adjacent rectangles traverse that edge in opposite directions, so the corresponding integrals cancel. Thus only the integral along the outer boundary remains, and it must also be zero.

Finally, a simple closed curve can be approximated by boundaries of unions of rectangles lying inside the region. Passing to the limit gives Cauchy’s theorem for simple closed curves.

Thus the triangular form proved by Goursat implies the full statement of Cauchy’s theorem for simple closed curves.


**Remark.**

There is a shorter proof of Cauchy’s theorem via Green’s theorem, reducing the result to the vanishing of certain partial derivatives. This approach, however, requires additional smoothness assumptions on the real and imaginary parts of $f$. Goursat’s argument is more subtle: it shows that complex differentiability alone suffices, with no prior assumption of continuity of the derivative. In this sense, the strength of Cauchy’s theorem lies not in the method of proof, but in the minimal nature of its hypotheses.

It is also worth noting that the theorem holds under weaker assumptions than those stated here. If $\Gamma$ is a simple closed curve in $D$, it suffices that $f$ be continuous on $\Gamma \cup \Gamma^i$ and holomorphic in the interior $\Gamma^i$ in order to conclude that $\int_\Gamma f(z)\,dz = 0$. This refinement, sometimes referred to as Pollard’s form, is rarely needed in applications.

## 3. Simply connected domains

We now turn to the geometric property of the domain underlying the theorem.

Intuitive description. A domain $D$ has no holes if every simple closed curve in $D$ encloses only points of $D$.

Formal definition. A domain $D$ is simply connected if every closed curve in $D$ can be continuously deformed to a point within $D$.

This condition captures the absence of holes in a precise topological sense.

## 4. The structural theorem

We now arrive at the central result which shows that Cauchy’s theorem is not merely a property of functions, but a characterization of the domain on which they are defined.

**Theorem.** Let $D \subset \mathbb{C}$ be a domain. The following are equivalent:

1. $D$ is simply connected,  
2. every holomorphic function on $D$ has a primitive,  
3. for every holomorphic $f$ on $D$ and every closed curve $\gamma \subset D$,

$$
\int_\gamma f(z)\,dz = 0.
$$

**Proof.** 

(2) ⇒ (3). If $f = F'$, then by the fundamental theorem of calculus,

$$
\int_\gamma f(z)\,dz = 0
$$

for every closed curve $\gamma$.

(3) ⇒ (2). Fix $z_0 \in D$ and define

$$
F(z) =
\int_\gamma f(w)\,dw,
$$

where $\gamma$ is any path from $z_0$ to $z$. We verify that $F$ is well-defined, that is, the value of the integral does not depend on the choice of path $\gamma$ from $z_0$ to $z$.

Let $\gamma_1$ and $\gamma_2$ be two paths from $z_0$ to $z$. Consider the closed curve obtained by following $\gamma_1$ from $z_0$ to $z$, and then $\gamma_2$ in reverse from $z$ back to $z_0$. Denote this closed curve by $\gamma_1 - \gamma_2$.

By hypothesis (3), since $f$ is holomorphic on $D$,

$$
\int_{\gamma_1 - \gamma_2} f(w)\,dw = 0.
$$

But

$$
\int_{\gamma_1 - \gamma_2} f(w)\,dw =
\int_{\gamma_1} f(w)\,dw -
\int_{\gamma_2} f(w)\,dw.
$$

Hence

$$
\int_{\gamma_1} f(w)\,dw =
\int_{\gamma_2} f(w)\,dw.
$$

Thus the value of $F(z)$ is independent of the choice of path, and $F$ is well-defined. Standard arguments now show that $F' = f$.

(1) ⇒ (3). This is Cauchy’s theorem.

(3) ⇒ (1). Suppose $D$ is not simply connected. Then there exists a point $a$ in a hole of $D$ and a closed curve $\gamma$ in $D$ winding around $a$.

Consider

$$
f(z) =
\frac{1}{z - a},
$$

which is holomorphic on $D$.

Then

$$
\int_\gamma \frac{1}{z - a}\,dz \ne 0,
$$

contradicting (3).

Thus $D$ must be simply connected.

$\square$


## 5. Geometric meaning

Cauchy’s theorem reveals that holomorphic functions cannot produce a nonzero integral along closed curves in regions without holes. Conversely, when a domain contains a hole, some holomorphic functions do produce nonzero integrals around closed curves.

Thus nonzero integrals reflect not a special feature of the function, but the topology of the domain in which it is defined. Complex integration thereby detects the presence of holes, and all holomorphic functions behave alike in regions without holes.

In the presence of holes, however,  holomorphic functions begin to distinguish themselves. Their integrals around closed curves need no longer agree, and different functions may produce different values on the same loop. Thus each function carries a global signature, detectable through integration. This is the starting point of residue theory, where such signatures are quantified and classified.


## 6. Closing perspective

A remarkable feature of Cauchy’s theorem is that it requires only the existence of the complex derivative. No continuity of the derivative is assumed.

Yet, through the Cauchy integral formula — a deeper result closely related to Cauchy’s theorem, expressing a holomorphic function in terms of its values on a surrounding curve — one finds that every holomorphic function possesses derivatives of all orders, and that these derivatives are themselves continuous, since each in turn admits a derivative.

Thus a minimal local assumption — complex differentiability at each point — forces a strong global conclusion: the function is infinitely differentiable.

---

## References

• A.-L. Cauchy, Sur les intégrales définies, Comptes Rendus de l’Académie des Sciences, 1846.

• E. Goursat, Sur la définition générale des fonctions analytiques, Annales Scientifiques de l’École Normale Supérieure, 1891.

• H. Haucha-Olsen, On Goursat’s proof of Cauchy’s integral theorem, American Mathematical Monthly, 115 (2008), 585–591.

• L. Ahlfors, Complex Analysis, 3rd ed., McGraw–Hill, 1979.

• T. W. Gamelin, Complex Analysis, Springer, 2001.

---

Cite as: ProofZoom Entry-0005, Cauchy’s Theorem and the Geometry of the Domain, ProofZoom (2026).

