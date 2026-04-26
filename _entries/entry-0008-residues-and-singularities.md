---
layout: entry
title: "Residues and Singularities"
entry_id: entry-0008
primary_area: Analysis
primary_subarea: Complex Analysis
difficulty: UG-Upper
published: 2026-04-24
updated:
permalink: /entries/entry-0008-residues-and-singularities/
pdf: /assets/pdfs/entry-0008-residues-and-singularities.pdf
abstract: "This entry explains how isolated singularities lead naturally to residues, and how residues measure the local contribution of a singularity to contour integrals."
---

## Overview

<!-- Replace this section with your content -->

This entry studies isolated singularities of holomorphic functions and introduces the residue as the coefficient that controls the contribution of a singularity to a contour integral.

---

## Key Idea

<!-- Replace this section with your content -->

Near an isolated singularity, a holomorphic function on a punctured neighborhood may be analyzed by its Laurent expansion. The coefficient of $(z-a)^{-1}$ plays a special role because it is the only term that contributes nontrivially to an integral around a small circle enclosing $a$.

---

## Isolated and Non-Isolated Singularities

Let $f$ be analytic in a region except at certain points where it fails to be defined or analytic. Such points are called **singularities** of $f$.

A singularity at a point $a$ is called **isolated** if there exists a small disk around $a$, say  
$$
0 < |z - a| < r,
$$
in which $f$ is analytic everywhere except possibly at $a$ itself.

In contrast, a singularity is **non-isolated** if every neighborhood of $a$ contains other singularities.

### Examples

- The function
  $$
  f(z) = \frac{1}{z}
  $$
  has an **isolated singularity** at $z = 0$, since it is analytic in every punctured disk around $0$.

- The function
  $$
  f(z) = \frac{1}{\sin(1/z)}
  $$
  has a **non-isolated singularity** at $z = 0$, since the zeros of $\sin(1/z)$ accumulate at $0$, producing infinitely many singularities arbitrarily close to it.

In this entry, we focus on **isolated singularities**, since they admit a precise and useful classification.

---

## Classification of Isolated Singularities

Let $f$ be analytic in a punctured neighborhood of $a$, that is, for $0 < \lvert z-a\rvert < r$. Then exactly one of the following occurs.

### 1. Removable Singularities

The singularity at $a$ is **removable** if $f$ can be extended to an analytic function at $a$.

Equivalently,
$$
\lim_{z \to a} f(z)
$$
exists and is finite.

#### Example

$$
f(z) = \frac{\sin z}{z}
$$

has a removable singularity at $z = 0$, since
$$
\lim_{z \to 0} \frac{\sin z}{z} = 1.
$$

Defining $f(0) = 1$ makes the function analytic at $0$.

---

### 2. Poles

The singularity at $a$ is a **pole** if $f(z) \to \infty$ as $z \to a$.

More precisely, $a$ is a pole of order $m$ if
$$
f(z) = \frac{g(z)}{(z-a)^m},
$$
where $g$ is analytic near $a$ and $g(a) \neq 0$.

#### Examples

- $$
  f(z) = \frac{1}{z}
  $$
  has a **simple pole** (order 1) at $z = 0$.

- $$
  f(z) = \frac{1}{z^2}
  $$
  has a pole of order 2 at $z = 0$.

---

### 3. Essential Singularities

If the singularity at $a$ is neither removable nor a pole, it is called **essential**.

These are the most irregular singularities: the function exhibits highly unstable behavior near $a$.

#### Example

$$
f(z) = e^{1/z}
$$

has an essential singularity at $z = 0$.

In any neighborhood of $0$, the function takes values that are dense in the complex plane (a consequence of the Casorati–Weierstrass theorem).

---

## Why This Classification Matters

This classification is not merely descriptive—it determines how a singularity contributes to contour integrals.

- Removable singularities contribute **nothing**.
- Poles contribute in a controlled, finite way.
- Essential singularities produce more complicated—but still precisely capturable—contributions.

The remarkable fact, which we develop next, is that **all of this information is encoded in a single coefficient in a local expansion**—the residue.


## Key Idea

Cauchy’s integral formula shows that if $f$ is analytic inside a closed curve $\gamma$, then
$$
f(a) = \frac{1}{2\pi i} \int_\gamma \frac{f(z)}{z-a}\,dz.
$$

This identity reveals a powerful principle: the value of $f$ at $a$ is encoded in the behavior of the function
$$
\frac{f(z)}{z-a}
$$
along the boundary curve.

Now suppose $f$ is not analytic at $a$, but is analytic in a punctured neighborhood
$$
0 < |z-a| < r.
$$

We can still ask: *what remains of Cauchy’s mechanism?*

---

### Local Expansion Near a Singular Point

In a punctured neighborhood of $a$, the function admits a **Laurent expansion**
$$
f(z) = \sum_{n=-\infty}^{\infty} c_n (z-a)^n.
$$

This expansion separates the behavior of $f$ into two parts:

- The **nonnegative powers** $(n \ge 0)$ form the analytic part.
- The **negative powers** $(n < 0)$ capture the singular behavior.

---

### What Survives Integration

Consider integrating $f$ around a small circle centered at $a$:
$$
\int_\gamma f(z)\,dz.
$$

Substituting the Laurent expansion and integrating term by term, we obtain:

- For $n \neq -1$,
  $$
  \int_\gamma (z-a)^n\,dz = 0.
  $$

- For $n = -1$,
  $$
  \int_\gamma \frac{1}{z-a}\,dz = 2\pi i.
  $$

Thus, **all terms vanish except one**.

---

### The Residue

The coefficient $c_{-1}$ plays a distinguished role. It is called the **residue** of $f$ at $a$:
$$
\operatorname{Res}(f,a) = c_{-1}.
$$

The integral becomes
$$
\int_\gamma f(z)\,dz = 2\pi i \cdot \operatorname{Res}(f,a).
$$

---

### Central Insight

Even when a function fails to be analytic at a point, its contribution to a contour integral is completely determined by a single number—the residue.

All other aspects of the function, including its regular part and higher-order singular behavior, cancel out under integration.

---

### From Local to Global

If a function has several isolated singularities inside a closed curve, each contributes independently through its residue.

This leads to a remarkable conclusion:

> A global contour integral is the sum of purely local contributions, one from each singularity.

This principle culminates in the **Residue Theorem**, which transforms the evaluation of integrals into a finite computation.

Let $f$ be holomorphic in a punctured disk $0<\vert z-a\rvert<r$. The point $a$ is called an isolated singularity of $f$.

If $f$ has a Laurent expansion
$$
f(z)=\sum_{n=-\infty}^{\infty} c_n (z-a)^n,
$$
then the residue of $f$ at $a$ is
$$
\operatorname{Res}(f,a)=c_{-1}.
$$

---

## Mathematical Formulation

We now formalize the ideas underlying singularities and residues.

---

### Laurent Expansion

Let $f$ be analytic in a punctured disk
$$
0 < |z-a| < r.
$$

Then $f$ admits a **Laurent expansion** about $a$:
$$
f(z) = \sum_{n=-\infty}^{\infty} c_n (z-a)^n,
$$
where the coefficients are given by
$$
c_n = \frac{1}{2\pi i} \int_\gamma \frac{f(z)}{(z-a)^{n+1}}\,dz,
$$
and $\gamma$ is any positively oriented simple closed curve contained in the punctured disk and enclosing $a$.

---

### Classification via the Laurent Expansion

The nature of the singularity at $a$ is completely determined by the negative-power part of the Laurent series:

- If $c_n = 0$ for all $n < 0$, the singularity is **removable**.

- If there exists $m \ge 1$ such that
  $$
  c_{-m} \neq 0, \quad \text{and} \quad c_n = 0 \text{ for all } n < -m,
  $$
  then $a$ is a **pole of order $m$**.

- If infinitely many coefficients $c_{-n}$ are nonzero, the singularity is **essential**.

---

### Residue

The coefficient
$$
c_{-1}
$$
is called the **residue** of $f$ at $a$, denoted
$$
\operatorname{Res}(f,a).
$$

It is given explicitly by
$$
\operatorname{Res}(f,a)
=
\frac{1}{2\pi i} \int_\gamma f(z)\,dz.
$$

---

### Residues at Poles

If $a$ is a pole of order $m$, then the residue can be computed by the formula
$$
\operatorname{Res}(f,a)
=
\frac{1}{(m-1)!}
\lim_{z \to a}
\frac{d^{\,m-1}}{dz^{\,m-1}}
\left[(z-a)^m f(z)\right].
$$

In particular, if $a$ is a simple pole ($m=1$), then
$$
\operatorname{Res}(f,a)
=
\lim_{z \to a} (z-a) f(z).
$$

---

### Residue Theorem

Let $f$ be analytic in a region except for finitely many isolated singularities $a_1, \dots, a_n$ inside a positively oriented simple closed curve $\gamma$.

Then
$$
\int_\gamma f(z)\,dz
=
2\pi i \sum_{k=1}^n \operatorname{Res}(f,a_k).
$$

---

This result reduces the evaluation of contour integrals to the computation of residues at isolated singularities.

## Proof Idea

The Residue Theorem rests on two simple observations.

First, away from its singularities, the function is analytic. Therefore, by Cauchy's theorem, the integral over a large contour can be deformed as long as we do not cross a singularity.

Second, near each isolated singularity, the Laurent expansion shows exactly what the singularity contributes.

Let $a$ be an isolated singularity of $f$. In a punctured disk around $a$, write
$$
f(z)=\sum_{n=-\infty}^{\infty} c_n(z-a)^n.
$$

If $\gamma_a$ is a small positively oriented circle around $a$, then
$$
\int_{\gamma_a} f(z)\,dz
=
\sum_{n=-\infty}^{\infty} c_n
\int_{\gamma_a} (z-a)^n\,dz.
$$

But
$$
\int_{\gamma_a} (z-a)^n\,dz=0
\quad \text{for } n\neq -1,
$$
while
$$
\int_{\gamma_a} \frac{1}{z-a}\,dz=2\pi i.
$$

Thus
$$
\int_{\gamma_a} f(z)\,dz
=
2\pi i\,c_{-1}
=
2\pi i\,\operatorname{Res}(f,a).
$$

Now suppose the singularities inside $\gamma$ are
$$
a_1,\dots,a_n.
$$

Remove small disjoint disks around these points. On the remaining region, $f$ is analytic. Hence Cauchy's theorem applies to the boundary of this punctured region.

The boundary consists of the outer curve $\gamma$ together with the small inner circles, each taken with the opposite orientation. Therefore,
$$
\int_\gamma f(z)\,dz
-
\sum_{k=1}^n \int_{\gamma_k} f(z)\,dz
=
0.
$$

Hence
$$
\int_\gamma f(z)\,dz
=
\sum_{k=1}^n \int_{\gamma_k} f(z)\,dz.
$$

Using the local computation at each singularity gives
$$
\int_\gamma f(z)\,dz
=
2\pi i
\sum_{k=1}^n \operatorname{Res}(f,a_k).
$$

This is the Residue Theorem.

The global integral over $\gamma$ is therefore reduced to a sum of local contributions, one from each singularity inside the curve.


## Main Theorem

<!-- Replace this section with your content -->

**Theorem.**  
If $f$ is holomorphic in a punctured disk around $a$ and has residue $\operatorname{Res}(f,a)$ at $a$, then for every sufficiently small positively oriented circle $\gamma$ around $a$,
$$
\int_\gamma f(z)\,dz = 2\pi i\,\operatorname{Res}(f,a).
$$

---

## Proof

## Proof

Let $f$ be analytic in a region except for finitely many isolated singularities
$$
a_1, a_2, \dots, a_n
$$
inside a positively oriented simple closed curve $\gamma$.

---

### Step 1. Excluding the Singular Points

Choose small disks centered at each $a_k$, with boundaries $\gamma_k$, such that:

- the disks are pairwise disjoint,
- each $\gamma_k$ is positively oriented,
- all disks lie entirely inside $\gamma$.

Let $D'$ be the region obtained by removing these disks from the interior of $\gamma$.

Then $f$ is analytic on $D'$.

---

### Step 2. Applying Cauchy’s Theorem

The boundary of $D'$ consists of:

- the outer curve $\gamma$ (positively oriented),
- the inner curves $\gamma_k$, each traversed in the **negative** direction.

Thus, by Cauchy’s theorem,
$$
\int_\gamma f(z)\,dz
-
\sum_{k=1}^n \int_{\gamma_k} f(z)\,dz
=
0.
$$

Hence,
$$
\int_\gamma f(z)\,dz
=
\sum_{k=1}^n \int_{\gamma_k} f(z)\,dz.
$$

---

### Step 3. Local Computation Near Each Singular Point

Fix a singularity $a_k$. Since $f$ is analytic in a punctured neighborhood of $a_k$, it has a Laurent expansion
$$
f(z)=\sum_{n=-\infty}^{\infty} c_n^{(k)} (z-a_k)^n.
$$

Integrating term by term around $\gamma_k$, we obtain
$$
\int_{\gamma_k} f(z)\,dz
=
\sum_{n=-\infty}^{\infty} c_n^{(k)}
\int_{\gamma_k} (z-a_k)^n\,dz.
$$

Now:

- If $n \neq -1$, then
  $$
  \int_{\gamma_k} (z-a_k)^n\,dz = 0.
  $$

- If $n = -1$, then
  $$
  \int_{\gamma_k} \frac{1}{z-a_k}\,dz = 2\pi i.
  $$

Therefore,
$$
\int_{\gamma_k} f(z)\,dz
=
2\pi i \, c_{-1}^{(k)}.
$$

---

### Step 4. Identifying the Residue

By definition,
$$
\operatorname{Res}(f,a_k) = c_{-1}^{(k)}.
$$

Thus,
$$
\int_{\gamma_k} f(z)\,dz
=
2\pi i \, \operatorname{Res}(f,a_k).
$$

---

### Step 5. Summing Contributions

Substituting into the expression from Step 2,
$$
\int_\gamma f(z)\,dz
=
\sum_{k=1}^n 2\pi i \, \operatorname{Res}(f,a_k)
=
2\pi i \sum_{k=1}^n \operatorname{Res}(f,a_k).
$$

---

### Conclusion

We have shown that
$$
\int_\gamma f(z)\,dz
=
2\pi i \sum_{k=1}^n \operatorname{Res}(f,a_k).
$$

This completes the proof of the Residue Theorem.

---

### Perspective

The proof makes transparent the central mechanism:

- Cauchy’s theorem reduces the problem to local integrals,
- the Laurent expansion isolates the singular behavior,
- only the $(z-a)^{-1}$ term survives integration.

Thus, a global contour integral is entirely determined by local data at the singularities.

---

## Examples and Computations of Residues

We now illustrate how residues are computed in practice and how they determine contour integrals.

---

### Example 1. A Simple Pole

Consider
$$
f(z) = \frac{1}{z}.
$$

The function has a simple pole at $z=0$. The residue is
$$
\operatorname{Res}(f,0) = \lim_{z \to 0} z \cdot \frac{1}{z} = 1.
$$

Thus, for any positively oriented simple closed curve $\gamma$ enclosing $0$,
$$
\int_\gamma \frac{1}{z}\,dz = 2\pi i.
$$

---

### Example 2. A Higher-Order Pole

Consider
$$
f(z) = \frac{1}{z^2}.
$$

This has a pole of order 2 at $z=0$. Its Laurent expansion contains no $(z-0)^{-1}$ term, so
$$
\operatorname{Res}(f,0) = 0.
$$

Hence,
$$
\int_\gamma \frac{1}{z^2}\,dz = 0.
$$

This shows that not all poles contribute nonzero residues.

---

### Example 3. A Rational Function

Consider
$$
f(z) = \frac{1}{z(z-1)}.
$$

This function has simple poles at $z=0$ and $z=1$.

- At $z=0$:
  $$
  \operatorname{Res}(f,0)
  =
  \lim_{z \to 0} z \cdot \frac{1}{z(z-1)}
  =
  \frac{1}{-1}
  =
  -1.
  $$

- At $z=1$:
  $$
  \operatorname{Res}(f,1)
  =
  \lim_{z \to 1} (z-1) \cdot \frac{1}{z(z-1)}
  =
  \frac{1}{1}
  =
  1.
  $$

Thus, if $\gamma$ encloses both singularities,
$$
\int_\gamma \frac{1}{z(z-1)}\,dz
=
2\pi i \,(-1 + 1)
=
0.
$$

If $\gamma$ encloses only one of them, the integral is determined by the corresponding residue.

---

### Example 4. Using the Derivative Formula

Consider
$$
f(z) = \frac{1}{(z-1)^2}.
$$

This has a pole of order 2 at $z=1$. Using the residue formula,
$$
\operatorname{Res}(f,1)
=
\frac{1}{1!}
\lim_{z \to 1}
\frac{d}{dz}\left[(z-1)^2 \cdot \frac{1}{(z-1)^2}\right]
=
\frac{d}{dz}(1)
=
0.
$$

Thus,
$$
\int_\gamma \frac{1}{(z-1)^2}\,dz = 0.
$$

---

### Example 5. An Essential Singularity

Consider
$$
f(z) = e^{1/z}.
$$

Using the series expansion
$$
e^{1/z} = \sum_{n=0}^\infty \frac{1}{n!} z^{-n},
$$
we identify the coefficient of $z^{-1}$:
$$
\frac{1}{1!} = 1.
$$

Thus,
$$
\operatorname{Res}(f,0) = 1,
$$
and
$$
\int_\gamma e^{1/z}\,dz = 2\pi i.
$$

---

### Example 6. A Function Regular at the Point

Consider
$$
f(z) = \sin z.
$$

This function is analytic everywhere, so it has no singularities. Therefore,
$$
\operatorname{Res}(f,a) = 0 \quad \text{for all } a,
$$
and
$$
\int_\gamma \sin z \, dz = 0
$$
for every closed curve $\gamma$.

---

## Summary of Techniques

In practice, residues are computed using:

- Limits for simple poles:
  $$
  \operatorname{Res}(f,a) = \lim_{z \to a} (z-a)f(z)
  $$

- Derivative formulas for higher-order poles

- Series expansions when available

These methods reduce contour integrals to explicit calculations.
## Discussion / Remarks

<!-- Replace this section with your content -->

The residue is a local quantity, but it determines the contribution of the singularity to contour integrals. This is the bridge from Cauchy’s integral formula to the residue theorem.

---
## Closing Perspective

The residue theorem reveals a striking principle at the heart of complex analysis:

> A global contour integral is completely determined by local data at singular points.

Cauchy’s theorem tells us that analytic functions contribute nothing to a closed contour integral. What remains, therefore, is entirely due to the failure of analyticity—and this failure is concentrated at isolated singularities.

The Laurent expansion makes this precise. Near each singularity, the function decomposes into a regular part and a singular part. Under integration, all terms vanish except one: the coefficient of $(z-a)^{-1}$. This single number—the residue—captures the entire contribution of the singularity.

In this way, complex integration becomes a theory of localization. A contour enclosing a region does not “feel” the function everywhere inside it; it detects only the singular points, and even there, only through a single coefficient.

This phenomenon also reflects the geometry of the domain. Singularities act as obstructions—points around which the function cannot be made analytic. The integral measures these obstructions, and the residue quantifies their effect.

Thus, the residue theorem completes a progression:

- Cauchy’s theorem: analytic functions have zero integral,
- Cauchy’s integral formula: values are determined by boundary behavior,
- Residue theorem: singularities contribute in discrete, computable units.

Together, these results reveal a deep unity between local behavior and global structure—a theme that runs throughout complex analysis.
## References

<!-- Replace this section with your content -->

[1] L. V. Ahlfors, *Complex Analysis*, 3rd ed., McGraw–Hill, 1979.  
[2] J. B. Conway, *Functions of One Complex Variable I*, 2nd ed., Springer, 1978.

---

## Cite as

<!-- Replace this section with your content -->

ProofZoom Entry-0008, *Residues and Singularities*, ProofZoom (2026).