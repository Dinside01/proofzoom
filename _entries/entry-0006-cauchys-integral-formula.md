---
layout: entry
title: "Cauchy's Integral Formula"
entry_id: entry-0006
primary_area: Complex Analysis
primary_subarea: Complex Integration
difficulty: UG-Upper

published: 2026-04-10
updated:

permalink: /entries/entry-0006-cauchys-integral-formula/

pdf: /assets/pdfs/entry-0006-cauchys-integral-formula.pdf

abstract: "Cauchy’s integral formula expresses the value of an analytic function at a point in terms of its values on a surrounding curve. The proof proceeds by isolating the contribution of a single interior point: an auxiliary function is constructed so that its contour integral vanishes, either by boundedness near the point or by a sharper decay condition. This reveals that the entire integral is governed by the local behavior of the integrand near that point. Consequently, analytic functions are determined by their boundary values and exhibit strong regularity properties."

---

## 1. Introduction

An important consequence of Cauchy's Theorem is the representation of an analytic function as a line integral. The representation, known as Cauchy's Integral formula, immediately shows that a differentiable complex function is in fact infinitely differentiable. The formula also helps in the study of the local properties of an analytic function.

We call an open subset $D$ of the complex plane a region if any two points of $D$ can be joined by a polygonal path comprising points of $D$. A function $f$ that is differentiable at every point in a region $D$ is indicated as $f \in H(D)$. A simple closed path will be abbreviated as *scp*. We denote the interior and exterior regions of a scp $\Gamma$ as $\Gamma^i$ and $\Gamma^e$, respectively.

We begin by extending Cauchy’s theorem from a single scp to configurations involving several such paths. This extension will allow us to isolate points inside a curve and ultimately lead to the integral formula.

---

## 2. Cauchy's Theorem for a sum of simple closed paths

A configuration comprising an scp $\Gamma$ and one or more scp's $\Gamma_j$ with each $\Gamma_j$ inside $\Gamma$ but outside the other $\Gamma_k$ (that is, $\Gamma_j \subset \Gamma_k^e \cap \Gamma^i$) can be represented as a single scp that is a sum of all the scp's, as would become clear in the proof of the theorem below.

**Theorem 2.1.**  
Let $C$ and $\Gamma$ be positively oriented scp's with $C \subset \Gamma^i$. Let $f \in H(D)$ and $D$ contain the closure of the region $\Gamma^i \cap C^e$. Then

$$
\int_{\Gamma} f(z)\,dz = \int_{C} f(z)\,dz.
$$

*Idea of the proof:* We connect the curves by auxiliary arcs so as to decompose the region between them into two simply connected regions, each bounded by a simple closed path lying in $D$. Applying Cauchy’s theorem to each gives the result.

**Proof.**  
Figure 1(a) (see the PDF version for the diagram)) shows oriented auxiliary arcs $A_1$ and $A_2$ joining the curves in $\Gamma^i \cap C^e$.  
Figure 1(b) shows Figure 1(a) split for illustration only. Let $\gamma_1 = \Gamma_1 - A_1^+ - C_1 + A_2^+$ and $\gamma_2 = \Gamma_2 - A_2^- - C_2 + A_1^-$. Each curve $\gamma_k$ is obtained by combining portions of $\Gamma$ and $C$ with auxiliary arcs that lie entirely in the region $\Gamma^i \cap C^e \subset D$. Hence every point enclosed by $\gamma_k$ lies in $D$, so Cauchy's theorem applies: $\int_{\gamma_k} f(z)\,dz = 0$, for $k = 1,2.$ Since $\gamma_1 + \gamma_2 = \Gamma_1 + \Gamma_2 - C_1 - C_2 = \Gamma - C$, we obtain $\int_{\Gamma - C} f(z)\,dz = 0$, as desired.

After the slit is introduced, the resulting curves are no longer smooth at the endpoints of the slit. These points are corners, and the curves are therefore only piecewise smooth. This level of regularity is sufficient for the validity of contour integration.


**Theorem 2.2 (Cauchy's theorem on sum of scp's).**  
Let $\Gamma_1,\dots, \Gamma_n$ and $\Gamma$ be positively oriented scp's such that $\Gamma_j \subset \Gamma_k^e$ if $j \ne k,$ and $\Gamma_j \subset \Gamma^i$ for $j = 1,\dots, n$. Then $\mathbb{E} = \Gamma^i \cap \Gamma_1^e \cap \dots \cap \Gamma_n^e$ is a region. If $D$ is a region containing the closure of $\mathbb{E}$ and if $f \in H(D)$, then

$$
\int_{\Gamma} f(z)\,dz = \sum_{j=1}^n \int_{\Gamma_j} f(z)\,dz.
$$

(The proof proceeds by induction on $n$, repeatedly applying Theorem 2.1 to remove one inner curve at a time. We omit the details.)

---

## 3. An extension of Cauchy's theorem

Here we consider the multi-curve version of Cauchy's theorem. This allows us to remove small neighborhoods of finitely many points inside $\Gamma$, reducing the study of integrals to arbitrarily small contours around those points.

**Lemma 3.1.**  
Let $\Gamma$ be a simple closed path such that $\Gamma \cup \Gamma^i$ is contained in a region $D \subset \mathbb{C}$. Let $z_1,\dots, z_n$ be points in $\Gamma^i$ and let $D^\ast$ be the region obtained by deleting these points from $D$. Let $f \in H(D^\ast)$ and suppose that there exists $\delta > 0$ such that $f$ is bounded in a deleted neighborhood $N'_{\delta}(z_j)$ for each $z_j$. Then

$$
\int_{\Gamma} f(z)\,dz = 0.
$$

*Idea of the proof.*  
We remove small circles around each deleted point and apply Theorem 2.2. The integral over $\Gamma$ is then expressed as a sum of integrals over these small circles, which can be made arbitrarily small.

**Proof.**  
Let $\epsilon > 0$. If $\lvert f(z) \rvert < M$ in each $N'_{\delta}(z_j)$, consider circles $\Gamma_j \subset \Gamma^i$ centered at each $z_j$ and of radius $r$, where $r$ is chosen less than $\delta$ so small that no two $\Gamma_j$ meet, and so that $r < \frac{\epsilon}{2\pi M n}$.

From Theorem 2.2,
$$
\int_{\Gamma} f(z)\,dz = \sum_{j=1}^n \int_{\Gamma_j} f(z)\,dz.
$$

From Theorem 4.1 in \cite{Pz0003},
$$
\left| \int_C f(z)\,dz \right| \le \int_C \lvert f \rvert ds \le (M \cdot \text{length of } C)
$$
for a smooth curve $C$.

Hence we have

$$
\left| \int_{\Gamma} f(z)\,dz \right|
\le \sum_{j=1}^n \left| \int_{\Gamma_j} f(z)\,dz \right|
\le n \cdot M \cdot (2\pi r) < \epsilon.
$$

It follows that
$$
\int_{\Gamma} f(z)\,dz = 0.
$$

Thus, finitely many isolated points at which $f$ is bounded do not contribute to the value of the integral.

Consequently, the study of contour integrals is reduced to understanding the contribution from arbitrarily small contours surrounding individual points. The next step is therefore to analyze what happens near a single point inside $\Gamma$.

The preceding lemma uses boundedness near the deleted points. A related and useful condition is that $(z - z_j) f(z) \to 0$, which ensures that the contribution from small circles vanishes.

**Lemma 3.2**  
Let $D$ be a region, and let $\Gamma$ be a positively oriented simple closed path such that $\Gamma \cup \Gamma_i \subset D$. Let $z_1,\dots,z_n$ be points in $\Gamma_i$, and set

$$
D^* = D \setminus \{z_1,\dots,z_n\}.
$$

Suppose $f \in H(D^*)$, and assume that for each $j = 1,\dots,n$,

$$
\lim_{z \to z_j} (z - z_j) f(z) = 0.
$$

Then

$$
\int_\Gamma f(z)\,dz = 0.
$$

**Idea of the proof.**  
We remove small circles around each deleted point and apply the multi-curve version of Cauchy’s theorem. The hypothesis implies that $f(z)$ grows more slowly than $1/|z - z_j|$, so the contribution from each small circle tends to zero.

**Proof.**  
Let $\varepsilon > 0$. For each $j = 1,\dots,n$, the condition

$$
\lim_{z \to z_j} (z - z_j) f(z) = 0
$$

implies that there exists $\delta_j > 0$ such that

$$
|(z - z_j) f(z)| < \frac{\varepsilon}{2\pi n}
\quad \text{whenever } 0 < |z - z_j| < \delta_j.
$$

Choose $r > 0$ small enough that $r < \delta_j$ for all $j$, and such that the circles

$$
\Gamma_j = \{ z : |z - z_j| = r \}
$$

are pairwise disjoint and lie entirely inside $\Gamma_i$.

By Theorem 2.2,

$$
\int_\Gamma f(z)\,dz = \sum_{j=1}^n \int_{\Gamma_j} f(z)\,dz.
$$

On each $\Gamma_j$, we have $\lvert z - z_j\rvert = r$, so

$$
|f(z)| = \frac{|(z - z_j) f(z)|}{|z - z_j|}
< \frac{\varepsilon}{2\pi n r}.
$$

Hence, using the estimate for contour integrals,

$$
\left| \int_{\Gamma_j} f(z)\,dz \right|
\le \max_{\Gamma_j} |f| \cdot \text{length}(\Gamma_j)
\le \frac{\varepsilon}{2\pi n r} \cdot (2\pi r)
= \frac{\varepsilon}{n}.
$$

Summing over $j$,

$$
\left| \int_\Gamma f(z)\,dz \right|
\le \sum_{j=1}^n \left| \int_{\Gamma_j} f(z)\,dz \right|
< \varepsilon.
$$

Since $\varepsilon > 0$ is arbitrary, it follows that

$$
\int_\Gamma f(z)\,dz = 0.
$$

---

## 4. Cauchy's Integral

Let $f \in H(D)$, and let $\Gamma$ be a simple closed curve in $D$. Let $a$ lie inside $\Gamma$. Define

$$
F(z)=\frac{f(z)-f(a)}{z-a},
\qquad z \in D \setminus \{a\}.
$$

Since $f$ is analytic in $D$, the function $F$ is analytic on $D \setminus \{a\}$.

Moreover,

$$
(z-a)F(z)=f(z)-f(a).
$$

Since $f$ is continuous at $a$, we have

$$
\lim_{z \to a} (z-a)F(z)
=
\lim_{z \to a}\bigl(f(z)-f(a)\bigr)
=0.
$$

Thus $F \in H(D \setminus \{a\})$, and the condition

$$
\lim_{z \to a}(z-a)F(z)=0
$$

shows that $F$ satisfies the hypothesis of Lemma 3.2 (with the single omitted point $a$). It follows that

$$
\int_{\Gamma} F(z)\,dz=0.
$$

Hence

$$
\int_{\Gamma}\frac{f(z)-f(a)}{z-a}\,dz=0,
$$

so

$$
\int_{\Gamma}\frac{f(z)}{z-a}\,dz
-
f(a)\int_{\Gamma}\frac{1}{z-a}\,dz
=0.
$$

Therefore

$$
\int_{\Gamma}\frac{f(z)}{z-a}\,dz
=
f(a)\int_{\Gamma}\frac{1}{z-a}\,dz.
$$

By the evaluation of the basic integral,

$$
\int_{\Gamma}\frac{1}{z-a}\,dz=2\pi i.
$$

Substituting this gives

$$
\boxed{
f(a)=\frac{1}{2\pi i}\int_{\Gamma}\frac{f(z)}{z-a}\,dz.
}
$$

**Key idea.**  
The auxiliary function

$$
F(z)=\frac{f(z)-f(a)}{z-a}
$$

may fail to be defined at $a$, but its singularity there is mild enough that Lemma 3.2 applies: the quantity $(z-a)F(z)$ tends to $0$. Thus the integral of $F$ around $\Gamma$ vanishes, and this isolates the desired formula for $f(a)$.

---

**Remark (Alternative proof via Lemma 3.1).**  
There is a second route to Cauchy’s integral formula using the removable singularity result (Lemma 3.1).

Define

$$
F(z)=\frac{f(z)-f(a)}{z-a}, \qquad z \in D \setminus \{a\}.
$$

Then $F \in H(D \setminus \{a\})$, and

$$
\lim_{z \to a} F(z)=f'(a).
$$

To verify boundedness near $a$, note that since the limit exists, there is $\delta>0$ such that

$$
\left| \frac{f(z)-f(a)}{z-a} - f'(a) \right| < 1
\quad \text{whenever } 0<|z-a|<\delta.
$$

Hence, for $0<\lvert z-a\rvert<\delta$,

$$
\left| \frac{f(z)-f(a)}{z-a} \right|
\le
\left| \frac{f(z)-f(a)}{z-a} - f'(a) \right| + |f'(a)|
< 1 + |f'(a)|.
$$

Thus $F$ is bounded in a deleted neighborhood of $a$.

Since $F \in H(D \setminus \{a\})$ and is bounded near $a$, Lemma 3.1 applies, and we conclude that

$$
\int_{\Gamma} F(z)\,dz=0.
$$

The remainder of the argument proceeds as before, yielding

$$
f(a)=\frac{1}{2\pi i}\int_{\Gamma}\frac{f(z)}{z-a}\,dz.
$$

**Comparison.**  
This proof uses boundedness near the singularity to conclude that its contribution to the integral vanishes. In contrast, the proof using Lemma 3.2 replaces boundedness by the sharper condition $(z-a)F(z)\to 0$, avoiding even this estimate. The latter approach is therefore more economical.

---

## 5. Closing perspective

Cauchy’s integral formula reveals a remarkable principle: the value of an analytic function inside a curve is completely determined by its values on the curve. The function carries no hidden interior freedom.

At the same time, the proof isolates a deeper phenomenon. The behavior of the function

$$
\frac{f(z)}{z-a}
$$

near the point $a$ governs the entire integral. In particular, the contribution of a single point can be detected through a contour integral.

This perspective leads naturally to the classification of isolated singularities and residues.

---

## References

- A.-L. Cauchy, *Sur les intégrales définies*, Comptes Rendus de l’Académie des Sciences, 1846.  
- L. V. Ahlfors, *Complex Analysis*, 3rd ed., McGraw–Hill, 1979.  
- ProofZoom Entry-0003, *Line integrals on rectifiable curves*, ProofZoom (2026).

---

**Cite as:** ProofZoom Entry-0006, *Cauchy's Integral Formula*, ProofZoom (2026).