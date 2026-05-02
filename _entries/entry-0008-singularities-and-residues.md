---
layout: entry
title: "Singularities and Residues"
entry_id: entry-0008
primary_area: "Complex Analysis"
primary_subarea: "Singularities and Residues"
difficulty: "UG-Upper"
published: 2026-04-22
updated:
permalink: /entries/entry-0008-singularities-and-residues/
pdf: /assets/pdfs/entry-0008-singularities-and-residues.pdf
abstract: "Singularities encode precise structural information about analytic functions. We classify isolated singularities using boundedness via Riemann's removable singularity theorem, explain how Taylor and Laurent expansions arise from this viewpoint, and show why residues are the part of a singularity detected by contour integration."
---

## 1. Overview

Singularities are among the most subtle objects in complex analysis. A function that is analytic in a region can fail to be analytic at isolated points. Understanding how this failure occurs is the key to understanding the function itself.

At first encounter, singularities may appear as pathologies. The central insight, however, is the following:

> *A singularity is not merely a failure of analyticity. It encodes precise structural information about the function.*

This entry follows that idea through three stages. First, boundedness separates removable singularities from genuine ones. Second, Laurent expansions record the remaining singular behavior algebraically. Third, contour integration detects exactly one Laurent coefficient: the residue.

## 2, Singularities

Let $f$ be analytic in a region except at certain points where it fails to be defined or analytic. Such points are called *singularities* of $f$.

A singularity at a point $a$ is called *isolated* if there exists a small disk around $a$, say

$$
0<|z-a|<r,
$$

in which $f$ is analytic everywhere except possibly at $a$ itself.

In contrast, a singularity is *non-isolated* if every neighborhood of $a$ contains other singularities.

**Examples.**

- The function

$$
f(z)=\frac{1}{z}
$$

  has an isolated singularity at $z=0$, since it is analytic in every punctured disk around $0$.

- The function

$$
f(z)=\frac{1}{\sin(1/z)}
$$

  has a non-isolated singularity at $z=0$, since the zeros of $\sin(1/z)$ accumulate at $0$, producing infinitely many singularities arbitrarily close to it.

Here we focus on isolated singularities, since they admit a precise and useful classification.

## 3. Singularities and local boundedness

Let $a$ be a point in the complex plane, and suppose that $f$ is defined in a punctured disk

$$
0<|z-a|<r.
$$

We say that $f$ is *locally bounded at $a$* if there are constants $M>0$ and $\delta>0$ such that

$$
|f(z)|\le M
\quad\text{whenever}\quad
0<|z-a|<\delta.
$$

For an arbitrary function, local boundedness immediately implies

$$
\lim_{z\to a}(z-a)f(z)=0.
$$

Indeed, if $\lbrace f(z)\rbrace\le M$ for $0<\lbrace z-a\rbrace <\delta$, then

$$
\lbrace (z-a)f(z)\rbrace \le M|z-a|,
$$

and the right-hand side tends to $0$ as $z\to a$.

The converse is not true for arbitrary functions. For example,

$$
f(z)=\frac{1}{\sqrt{\lbrace z-a\rbrace }}
$$

is unbounded near $a$, but

$$
|(z-a)f(z)|=\sqrt{|z-a|}\to 0.
$$

Thus, for general functions, the condition

$$
\lim_{z\to a}(z-a)f(z)=0
$$

does not force boundedness.

The remarkable fact is that, for holomorphic functions, the converse also holds. If $f$ is holomorphic in a punctured disk about $a$, then

$$
f \text{ is locally bounded at } a
\quad\Longleftrightarrow\quad
\lim_{z\to a}(z-a)f(z)=0.
$$

This equivalence is one reason local boundedness is the natural dividing line in the study of isolated singularities. In the holomorphic setting, boundedness is not merely a size condition. It is a rigidity condition. It tells us that the apparent singularity can actually be filled in.

We now prove the theorem that makes this precise.


**Theorem (Riemann's Removable Singularity Theorem).**


Let $f$ be holomorphic in a punctured disk
$$
0 < |z-a| < r.
$$
If $f$ is locally bounded at $a$, then there exists a holomorphic function $F$ on the full disk $|z-a|<r$ such that
$$
F(z)=f(z) \quad \text{for } 0<|z-a|<r.
$$


**Proof.**

Choose $0<\rho<r$, and let
$$
C=\{w : |w-a|=\rho\}
$$
be the positively oriented circle centered at $a$.

Fix a point $z$ with $0<|z-a|<\rho$. Throughout the proof, $w$ denotes the variable of integration along contours.
Let $0<\varepsilon<|z-a|/2$, and consider the inner circle
$$
C_\varepsilon=\{w : |w-a|=\varepsilon\},
$$
oriented positively. Then $z$ lies outside $C_\varepsilon$ and inside $C$.

On the annular region between $C_\varepsilon$ and $C$, the function
$$
\frac{f(w)}{w-z}
$$
is holomorphic except for a simple pole at $w=z$.

Applying Cauchy’s integral formula on this annulus, we obtain
$$
f(z)
=
\frac{1}{2\pi i}\int_C \frac{f(w)}{w-z}\,dw
-
\frac{1}{2\pi i}\int_{C_\varepsilon} \frac{f(w)}{w-z}\,dw.
$$

We now estimate the second integral. Since $f$ is locally bounded at $a$, there exist constants $M>0$ and $\delta>0$ such that
$$
|f(w)| \le M \quad \text{whenever } 0<|w-a|<\delta.
$$

Fix $z$ with $0<|z-a|<\rho$, and choose
$$
0<\varepsilon<\min\left\{\delta,\;\frac{|z-a|}{2}\right\}.
$$
Then the circle $C_\varepsilon=\{w:|w-a|=\varepsilon\}$ lies entirely within the region $0<|w-a|<\delta$, and for all $w\in C_\varepsilon$,
$$
|w-z| \ge |z-a| - |w-a| > \frac{|z-a|}{2}.
$$
Hence
$$
\left|\frac{f(w)}{w-z}\right|
\le
\frac{2M}{|z-a|}.
$$

Therefore,
$$
\left|
\int_{C_\varepsilon} \frac{f(w)}{w-z}\,dw
\right|
\le
(2\pi \varepsilon)\cdot \frac{2M}{|z-a|}
=
\frac{4\pi M \varepsilon}{|z-a|}.
$$

As $\varepsilon \to 0$, this tends to $0$. Thus,
$$
f(z)
=
\frac{1}{2\pi i}\int_C \frac{f(w)}{w-z}\,dw.
$$
for every $z$ with $0<|z-a|<\rho$.
Now define
$$
F(z)
=
\frac{1}{2\pi i}\int_C \frac{f(w)}{w-z}\,dw
\quad \text{for } \lbrace z-a\rbrace <\rho.
$$

Since $z$ lies strictly inside $C$, the integrand is holomorphic in $z$, and therefore $F$ is holomorphic on the disk $\lbrace z-a\rbrace <\rho$.

For $z\neq a$, we have already shown that $F(z)=f(z)$. Thus $F$ extends $f$ holomorphically across $a$.

Since $\rho<r$ was arbitrary, the extension exists on the full disk $|z-a|<r$.
$\square$

### The Riemann extension principle

The preceding theorem may be used as a principle:

> *If a function is holomorphic in a punctured neighborhood of $a$ and is locally bounded at $a$, then the value at $a$ can be supplied in exactly one way so that the function becomes holomorphic at $a$.*

Thus, after applying the theorem, we may regard the singularity as having been removed.

This also proves the promised holomorphic equivalence:

$$
f \text{ is locally bounded at } a
\quad\Longleftrightarrow\quad
\lim_{z\to a}(z-a)f(z)=0,
$$

provided $f$ is holomorphic in a punctured neighborhood of $a$.

We already proved the forward implication. Conversely, suppose

$$
\lim_{z\to a}(z-a)f(z)=0.
$$

Define

$$
g(z)=(z-a)f(z)
\quad\text{for}\quad
0<|z-a|<r.
$$

Then $g$ is holomorphic in the punctured disk and tends to $0$ as $z\to a$. In particular, $g$ is locally bounded at $a$. By Riemann's theorem, $g$ extends holomorphically to $a$, with extended value

$$
g(a)=0.
$$

Since the extended function $g$ is holomorphic and vanishes at $a$, we may write

$$
g(z)=(z-a)h(z)
$$

for some holomorphic function $h$ near $a$. Therefore, for $z\ne a$,

$$
f(z)=\frac{g(z)}{z-a}=h(z).
$$

Thus $f$ agrees near $a$, except possibly at $a$ itself, with a holomorphic function $h$. In particular, $f$ is locally bounded at $a$.

**Remark (Uniqueness of the extension).**  
The holomorphic extension in Riemann's theorem is unique.

Indeed, suppose $F$ and $G$ are both holomorphic on $\lbrace z-a\rbrace <r$ and both agree with $f$ on the punctured disk

$$
0<|z-a|<r.
$$

Then

$$
F(z)-G(z)=0
\quad\text{for}\quad
0<|z-a|<r.
$$

Since $F-G$ is continuous at $a$, we get

$$
F(a)-G(a)
=
\lim_{z\to a}(F(z)-G(z))
=0.
$$

Hence $F(a)=G(a)$. Away from $a$, the two functions already agree. Therefore $F=G$ on the whole disk.

So a removable singularity is not removed by making an arbitrary choice. Holomorphicity forces the missing value.

## 4. Classification of isolated singularities

Let $f$ be holomorphic in a punctured disk

$$
0<|z-a|<r.
$$

Then $a$ is an isolated singularity of $f$. Riemann's theorem gives the first possible type.

### Removable singularities

The singularity at $a$ is called *removable* if $f$ is locally bounded at $a$.

Equivalently, by Riemann's theorem, $f$ has a holomorphic extension to $a$.

For example,

$$
f(z)=\frac{\sin z}{z}
$$

has an isolated singularity at $0$, but the singularity is removable. The function becomes holomorphic at $0$ by defining

$$
f(0)=1.
$$

### Poles

The singularity at $a$ is called a *pole* if

$$
|f(z)|\to \infty
\quad\text{as}\quad
z\to a.
$$

For example,

$$
f(z)=\frac{1}{(z-a)^m},
\qquad m\ge 1,
$$

has a pole at $a$.

A pole is not removable, because a function that tends to infinity near $a$ certainly cannot be locally bounded there.

Equivalently, $a$ is a pole of $f$ if, in a punctured neighborhood of $a$, the reciprocal $1/f$ is defined, has a removable singularity at $a$, and its holomorphic extension takes the value $0$ at $a$.

### Essential singularities

If the singularity is neither removable nor a pole, it is called an *essential singularity*.

Thus an essential singularity is a point where the function is not locally bounded, but also does not tend to infinity.

For example,

$$
f(z)=e^{1/z}
$$

has an essential singularity at $0$.

Along the positive real axis, $e^{1/z}$ tends to infinity as $z\to 0$. Along the negative real axis, it tends to $0$. Hence the function does not have pole-like behavior. At the same time, it is not locally bounded near $0$. Therefore the singularity is essential.

Another fundamental example is

$$
f(z)=\sin\!\left(\frac{1}{z}\right),
$$

which oscillates infinitely often near $0$ and takes values arbitrarily close to every complex number.

### Structural principle

An isolated singularity is non-essential precisely when either the function or its reciprocal is controlled near the point. More precisely:

$$
\begin{array}{rcl}
f \text{ locally bounded at } a &\Longrightarrow& \text{removable},\\[3pt]
1/f \text{ locally bounded near } a \text{ and extending to } 0 &\Longrightarrow& \text{pole},\\[3pt]
\text{neither form of control applies} &\Longrightarrow& \text{essential}.
\end{array}
$$

Thus the trichotomy is not arbitrary. It is a boundedness trichotomy.
\section{A criterion for removability}

We record a useful characterization.

**Theorem**

Let $f$ be holomorphic in a punctured disk
$$
0<|z-a|<r.
$$
Then the isolated singularity at $a$ is removable if and only if
$$
\lim_{z\to a}(z-a)f(z)=0.
$$


**Proof.**

If the singularity is removable, then $f$ extends holomorphically to $a$. In particular, $f$ is locally bounded at $a$. Hence there are constants $M>0$ and $\delta>0$ such that
$$
|f(z)|\le M
\quad\text{whenever}\quad
0<|z-a|<\delta.
$$
Therefore
$$
|(z-a)f(z)|\le M|z-a|,
$$
and so
$$
\lim_{z\to a}(z-a)f(z)=0.
$$

Conversely, suppose
$$
\lim_{z\to a}(z-a)f(z)=0.
$$
By the holomorphic equivalence established above, this implies that $f$ is locally bounded at $a$. By Riemann's removable singularity theorem, $f$ extends holomorphically to $a$. Hence the singularity is removable.
$\square$


## 5. From removability to Taylor expansion

The criterion for removability also explains why Taylor expansions are natural in complex analysis.

Suppose $f$ is holomorphic at $a$. For $z\ne a$, consider

$$
F(z)=\frac{f(z)-f(a)}{z-a}.
$$

Then

$$
(z-a)F(z)=f(z)-f(a),
$$

and hence

$$
\lim_{z\to a}(z-a)F(z)=0.
$$

By the removability criterion, $F$ extends holomorphically to $a$. Since

$$
\lim_{z\to a}\frac{f(z)-f(a)}{z-a}=f'(a),
$$

the extended value is

$$
F(a)=f'(a).
$$

Define this extended function by

$$
f_1(z)=F(z).
$$

Then

$$
f(z)=f(a)+(z-a)f_1(z),
$$

where $f_1$ is holomorphic near $a$.

Now repeat the same process with $f_1$. For $z\ne a$, define

$$
f_2(z)=\frac{f_1(z)-f_1(a)}{z-a}.
$$

Again, the removability criterion shows that $f_2$ extends holomorphically to $a$, with

$$
f_2(a)=f_1'(a).
$$

Thus

$$
f_1(z)=f_1(a)+(z-a)f_2(z).
$$

Substituting this into

$$
f(z)=f(a)+(z-a)f_1(z),
$$

we obtain

$$
f(z)=f(a)+(z-a)f_1(a)+(z-a)^2f_2(z).
$$

Continuing inductively, we obtain holomorphic functions $f_n$ such that, for every $N\ge 0$,

$$
f(z)
=
f(a)
+(z-a)f_1(a)
+(z-a)^2f_2(a)
+\cdots
+(z-a)^N f_N(a)
+(z-a)^{N+1}f_{N+1}(z).
$$

The coefficients are precisely the Taylor coefficients:

$$
f_n(a)=\frac{f^{(n)}(a)}{n!}.
$$

Thus the repeated removal of singularities gives the Taylor expansion with a holomorphic remainder:

$$
f(z)
=
\sum_{n=0}^{N}
\frac{f^{(n)}(a)}{n!}(z-a)^n
+(z-a)^{N+1}f_{N+1}(z).
$$

Letting $N\to\infty$, together with the standard convergence theorem for Taylor series of holomorphic functions, gives

$$
f(z)
=
\sum_{n=0}^{\infty}
\frac{f^{(n)}(a)}{n!}(z-a)^n
$$

inside the disk of holomorphy.

**Remark.**
The Taylor expansion emerges from the repeated removal of singularities. At each step, the quotient
$$
\frac{f_k(z)-f_k(a)}{z-a}
$$
has a removable singularity at $a$, and removing it produces the next coefficient. Thus Taylor expansion is not merely a formal power series calculation; it is repeated analytic continuation across removable singularities.


## 6. Laurent expansions ##

The preceding section shows that when no singular behavior remains, repeated removability produces a Taylor expansion. But at an isolated singularity, some part of the function may resist removal.

Laurent expansions record exactly this remaining singular behavior. The nonnegative powers form the Taylor-like part; the negative powers record what cannot be removed.

\section{Laurent expansions}

Taylor expansions describe holomorphic functions near ordinary points. Laurent expansions describe holomorphic functions near isolated singularities.

**Theorem(Laurent expansion)**.

Let $f$ be holomorphic in the annulus
$$
0<|z-a|<R.
$$
Then there exist unique complex numbers $c_n$, $n\in\mathbb Z$, such that
$$
f(z)=\sum_{n=-\infty}^{\infty}c_n(z-a)^n
$$
for $0<|z-a|<R$.

Moreover, for any positively oriented circle
$$
|\zeta-a|=\rho,
\qquad 0<\rho<R,
$$
the coefficients are given by
$$
c_n=
\frac{1}{2\pi i}
\int_{|\zeta-a|=\rho}
\frac{f(\zeta)}{(\zeta-a)^{n+1}}\,d\zeta.
$$

We shall not prove the full Laurent theorem here. Instead, we use it to show how isolated singularities are encoded algebraically.

The terms with nonnegative powers,
$$
c_0+c_1(z-a)+c_2(z-a)^2+\cdots,
$$
form the \emph{regular part} of the expansion.

The terms with negative powers,
$$
\frac{c_{-1}}{z-a}
+
\frac{c_{-2}}{(z-a)^2}
+
\frac{c_{-3}}{(z-a)^3}
+\cdots,
$$
form the \emph{principal part}.

Thus the Laurent expansion separates two kinds of behavior:
- the regular part behaves like a Taylor series;
- the principal part measures the singular behavior at $a$.

This is the algebraic counterpart of the earlier boundedness classification.

### The principal part

The principal part is the part of the Laurent expansion responsible for the singularity.

If the principal part is absent, then

$$
f(z)=c_0+c_1(z-a)+c_2(z-a)^2+\cdots,
$$

so $f$ is represented by a Taylor series near $a$. The singularity is therefore removable.

If the principal part has finitely many nonzero terms, say

$$
\frac{c_{-m}}{(z-a)^m}
+
\frac{c_{-(m-1)}}{(z-a)^{m-1}}
+\cdots+
\frac{c_{-1}}{z-a},
\qquad c_{-m}\ne 0,
$$

then $f$ has a pole of order $m$ at $a$.

If the principal part has infinitely many nonzero terms, then the singularity is essential.

Thus the Laurent expansion gives the same trichotomy in algebraic form:

$$
\begin{array}{rcl}
\text{removable singularity} &\Longleftrightarrow& \text{no negative powers},\\[3pt]
\text{pole} &\Longleftrightarrow& \text{finitely many negative powers},\\[3pt]
\text{essential singularity} &\Longleftrightarrow& \text{infinitely many negative powers}.
\end{array}
$$

### Examples

**Example 1. A removable singularity.**  
Consider

$$
f(z)=\frac{\sin z}{z}
$$

at $z=0$. Since

$$
\sin z
=
z-\frac{z^3}{3!}+\frac{z^5}{5!}-\cdots,
$$

we have

$$
\frac{\sin z}{z}
=
1-\frac{z^2}{3!}+\frac{z^4}{5!}-\cdots.
$$

There are no negative powers. Hence the singularity at $0$ is removable.

**Example 2. A pole.**  
Consider

$$
f(z)=\frac{1}{z^m}
$$

at $z=0$. Its Laurent expansion is already visible:

$$
f(z)=z^{-m}.
$$

The principal part has exactly one term. Hence $0$ is a pole of order $m$.

More generally, if

$$
f(z)=\frac{g(z)}{(z-a)^m},
$$

where $g$ is holomorphic near $a$ and $g(a)\ne 0$, then $f$ has a pole of order $m$ at $a$.

Indeed, the Taylor expansion of $g$ has the form

$$
g(z)=g(a)+g_1(z-a)+g_2(z-a)^2+\cdots,
$$

and therefore

$$
f(z)
=
\frac{g(a)}{(z-a)^m}
+
\frac{g_1}{(z-a)^{m-1}}
+\cdots.
$$

The negative powers stop after finitely many terms.

**Example 3. An essential singularity.**  
Consider

$$
f(z)=e^{1/z}
$$

at $z=0$. Since

$$
e^w=1+w+\frac{w^2}{2!}+\frac{w^3}{3!}+\cdots,
$$

substituting $w=1/z$ gives

$$
e^{1/z}
=
1+\frac{1}{z}
+
\frac{1}{2!z^2}
+
\frac{1}{3!z^3}
+\cdots.
$$

The principal part has infinitely many nonzero terms. Hence $0$ is an essential singularity.

This example also agrees with the earlier behavioral classification. Along the positive real axis, $e^{1/z}\to\infty$. Along the negative real axis, $e^{1/z}\to 0$. Thus the singularity is not pole-like, and it is certainly not removable.

## 7. Residues ##

Among all the coefficients in the Laurent expansion, one coefficient plays a special role.

Let

$$
f(z)=\sum_{n=-\infty}^{\infty}c_n(z-a)^n
$$

be the Laurent expansion of $f$ in a punctured neighborhood of $a$.

The coefficient $c_{-1}$ is called the **residue** of $f$ at $a$. It is denoted by

$$
\operatorname{Res}(f,a)=c_{-1}.
$$

Thus the residue is the coefficient of

$$
\frac{1}{z-a}
$$

in the Laurent expansion.

At first this may look like just one coefficient among many. But it is exactly the coefficient detected by contour integration.

### Why the coefficient of $(z-a)^{-1}$ matters

Let $\gamma$ be a positively oriented circle centered at $a$:

$$
\gamma(t)=a+\rho e^{it},
\qquad 0\le t\le 2\pi.
$$

Then

$$
dz=i\rho e^{it}\,dt.
$$

For an integer $n$, consider

$$
\int_\gamma (z-a)^n\,dz.
$$

Substituting $z-a=\rho e^{it}$, we get

$$
\int_\gamma (z-a)^n\,dz
=
\int_0^{2\pi}(\rho e^{it})^n i\rho e^{it}\,dt.
$$

Hence

$$
\int_\gamma (z-a)^n\,dz
=
i\rho^{n+1}
\int_0^{2\pi}e^{i(n+1)t}\,dt.
$$

If $n\ne -1$, then $n+1\ne 0$, and

$$
\int_0^{2\pi}e^{i(n+1)t}\,dt=0.
$$

But if $n=-1$, then

$$
(z-a)^{-1}\,dz
=
\frac{1}{\rho e^{it}}i\rho e^{it}\,dt
=
i\,dt,
$$

so

$$
\int_\gamma \frac{1}{z-a}\,dz
=
\int_0^{2\pi}i\,dt
=
2\pi i.
$$

Therefore

$$
\int_\gamma (z-a)^n\,dz
=
\begin{cases}
0, & n\ne -1,\\[4pt]
2\pi i, & n=-1.
\end{cases}
$$

This is the fundamental reason residues matter: all Laurent terms disappear under integration around a small circle except the $(z-a)^{-1}$ term.

**Consequence**

If

$$
f(z)=\sum_{n=-\infty}^{\infty}c_n(z-a)^n,
$$

then integrating term by term around a small positively oriented circle gives

$$
\int_\gamma f(z)\,dz
=
2\pi i\,c_{-1}.
$$

That is,

$$
\int_\gamma f(z)\,dz
=
2\pi i\,\operatorname{Res}(f,a).
$$

This is the local form of the residue theorem.

> *Central insight. The residue is the part of a singularity detected by contour integration.*

## The residue theorem

### The local form

**Theorem (Local residue theorem).**  
Let $f$ be holomorphic in a punctured disk

$$
0<|z-a|<R,
$$

and let $\gamma$ be a positively oriented circle centered at $a$, small enough to lie inside the punctured disk. Then

$$
\int_\gamma f(z)\,dz
=
2\pi i\,\operatorname{Res}(f,a).
$$

**Proof.**  
Write the Laurent expansion

$$
f(z)=\sum_{n=-\infty}^{\infty}c_n(z-a)^n.
$$

On the circle $\gamma$, the Laurent series may be integrated term by term. Therefore

$$
\int_\gamma f(z)\,dz
=
\sum_{n=-\infty}^{\infty}c_n\int_\gamma (z-a)^n\,dz.
$$

But we have shown that

$$
\int_\gamma (z-a)^n\,dz=0
\quad\text{for } n\ne -1,
$$

while

$$
\int_\gamma (z-a)^{-1}\,dz=2\pi i.
$$

Hence

$$
\int_\gamma f(z)\,dz
=
2\pi i\,c_{-1}.
$$

Since $c_{-1}=\operatorname{Res}(f,a)$, we obtain

$$
\int_\gamma f(z)\,dz
=
2\pi i\,\operatorname{Res}(f,a).
$$

This proves the result. $\square$

### The residue theorem for several singularities

The local result extends to curves enclosing finitely many isolated singularities.

**Theorem (Cauchy's residue theorem).**  
Let $f$ be holomorphic in a region $D$ except for finitely many isolated singularities

$$
a_1,a_2,\ldots,a_N.
$$

Let $\gamma$ be a positively oriented simple closed curve such that $\gamma$ and its interior lie in $D$, and suppose that $\gamma$ avoids the singularities and that the singularities inside $\gamma$ are precisely

$$
a_1,a_2,\ldots,a_N.
$$

Then

$$
\int_\gamma f(z)\,dz
=
2\pi i
\sum_{j=1}^{N}\operatorname{Res}(f,a_j).
$$

**Proof.**  
Choose small disjoint positively oriented circles $C_j$ around the singularities $a_j$, all lying inside $\gamma$. Remove from the interior of $\gamma$ the disks bounded by these circles. On the remaining region, $f$ is holomorphic.

By Cauchy's theorem applied to this multiply connected region,

$$
\int_\gamma f(z)\,dz
-
\sum_{j=1}^{N}\int_{C_j}f(z)\,dz
=0.
$$

By the local residue theorem,

$$
\int_{C_j}f(z)\,dz
=
2\pi i\,\operatorname{Res}(f,a_j).
$$

Therefore

$$
\int_\gamma f(z)\,dz
=
2\pi i
\sum_{j=1}^{N}\operatorname{Res}(f,a_j).
$$

This proves the theorem. $\square$

The theorem says that the integral around the large curve is obtained by adding the local contributions from the singularities inside the curve. Each singularity contributes exactly one number: its residue.

### Geometric meaning

The residue theorem is a localization principle.

The integral of $f$ around a closed curve does not depend on all the details of $f$ throughout the enclosed region. It depends only on the $(z-a_j)^{-1}$ coefficients in the Laurent expansions at the singularities inside the curve.

Thus residues convert a global contour integral into a finite sum of local data:

$$
\text{global integral}
=
\text{sum of local singular contributions}.
$$

## Computing residues

The residue is defined as the coefficient of $(z-a)^{-1}$ in the Laurent expansion. In principle, therefore, one can always compute the residue by finding the Laurent expansion.

In practice, however, residues are often computed more directly.

### Residue at a simple pole

Suppose $f$ has a simple pole at $a$. Then the Laurent expansion has the form

$$
f(z)=\frac{c_{-1}}{z-a}+c_0+c_1(z-a)+\cdots.
$$

Multiplying by $z-a$, we get

$$
(z-a)f(z)
=
c_{-1}+c_0(z-a)+c_1(z-a)^2+\cdots.
$$

Therefore

$$
\lim_{z\to a}(z-a)f(z)=c_{-1}.
$$

Hence, if $f$ has a simple pole at $a$, then

$$
\operatorname{Res}(f,a)
=
\lim_{z\to a}(z-a)f(z).
$$

This is the most frequently used residue formula.

**Example.**  
Consider

$$
f(z)=\frac{1}{z^2+1}.
$$

The singularities occur where

$$
z^2+1=0,
$$

that is, at

$$
z=i
\quad\text{and}\quad
z=-i.
$$

At $z=i$, we have

$$
z^2+1=(z-i)(z+i).
$$

Thus

$$
f(z)=\frac{1}{(z-i)(z+i)}.
$$

Since $z=i$ is a simple pole,

$$
\operatorname{Res}(f,i)
=
\lim_{z\to i}(z-i)\frac{1}{(z-i)(z+i)}.
$$

Hence

$$
\operatorname{Res}(f,i)
=
\lim_{z\to i}\frac{1}{z+i}
=
\frac{1}{2i}.
$$

Similarly,

$$
\operatorname{Res}(f,-i)
=
\lim_{z\to -i}(z+i)\frac{1}{(z-i)(z+i)}
=
\lim_{z\to -i}\frac{1}{z-i}
=
-\frac{1}{2i}.
$$

Thus

$$
\operatorname{Res}(f,i)=\frac{1}{2i},
\qquad
\operatorname{Res}(f,-i)=-\frac{1}{2i}.
$$

### Simple poles of quotients

A common situation is this. Suppose

$$
f(z)=\frac{g(z)}{h(z)},
$$

where $g$ and $h$ are holomorphic near $a$, and suppose

$$
h(a)=0,
\qquad
h'(a)\ne 0.
$$

If $g(a)\ne 0$, then $f$ has a simple pole at $a$. More generally, the residue formula below remains valid whether or not $g(a)$ is zero.

Since

$$
h(z)=(z-a)H(z),
$$

where $H$ is holomorphic and

$$
H(a)=h'(a),
$$

we have

$$
f(z)=\frac{g(z)}{(z-a)H(z)}.
$$

Therefore

$$
(z-a)f(z)=\frac{g(z)}{H(z)}.
$$

Taking the limit as $z\to a$, we obtain

$$
\operatorname{Res}(f,a)
=
\frac{g(a)}{H(a)}
=
\frac{g(a)}{h'(a)}.
$$

Thus, if $h$ has a simple zero at $a$, then

$$
\operatorname{Res}\left(\frac{g}{h},a\right)
=
\frac{g(a)}{h'(a)}.
$$

\textbf{Example.}
Let
$$
f(z)=\frac{e^z}{z^2+1}.
$$
Again,
$$
z^2+1=(z-i)(z+i),
$$
so the singularities are $i$ and $-i$.
At $z=i$, take
$$
g(z)=e^z,
\qquad
h(z)=z^2+1.
$$
Then
$$
h'(z)=2z,
$$
so
$$
h'(i)=2i.
$$
Therefore
$$
\operatorname{Res}(f,i)
=
\frac{g(i)}{h'(i)}
=
\frac{e^i}{2i}.
$$
Similarly,
$$
\operatorname{Res}(f,-i)
=
\frac{e^{-i}}{-2i}.
$$

### Residue at a pole of higher order

Suppose $f$ has a pole of order $m$ at $a$. Then

$$
f(z)
=
\frac{c_{-m}}{(z-a)^m}
+\cdots+
\frac{c_{-2}}{(z-a)^2}
+
\frac{c_{-1}}{z-a}
+c_0+c_1(z-a)+\cdots.
$$

Multiplying by $(z-a)^m$, we get

$$
(z-a)^m f(z)
=
c_{-m}+c_{-(m-1)}(z-a)+\cdots+c_{-1}(z-a)^{m-1}+\cdots.
$$

The coefficient $c_{-1}$ is therefore the coefficient of $(z-a)^{m-1}$ in the Taylor expansion of $(z-a)^m f(z)$. Hence

$$
\operatorname{Res}(f,a)
=
\frac{1}{(m-1)!}
\lim_{z\to a}
\frac{d^{m-1}}{dz^{m-1}}
\left((z-a)^m f(z)\right).
$$

This formula is useful, but the conceptual point is simpler:

> To find the residue at a pole, remove the pole by multiplying by the appropriate power of $z-a$, and then read off the correct Taylor coefficient.*

## 8. Closing perspective

The theory of isolated singularities moves from behavior to algebra to integration.

First, boundedness distinguishes removable singularities from genuine ones. Then Laurent expansions encode the singular behavior algebraically in the principal part. Finally, contour integration detects exactly one coefficient of that principal part: the coefficient of $(z-a)^{-1}$.

Thus the residue is not an arbitrary coefficient. It is the part of the singularity visible to closed contour integration. The residue theorem says that a global integral is obtained by summing these local visible parts.

In this sense, residues are the bridge between local singular behavior and global contour integrals.

## References

[1] A.-L. Cauchy, *Mémoire sur les intégrales définies, prises entre des limites imaginaires*, Paris: De Bure frères, 1825.

[2] P. A. Laurent, *Mémoire sur le calcul des variations*, submitted to the Académie des Sciences, 1843. This memoir contains the expansion now called the Laurent series.

[3] L. V. Ahlfors, *Complex Analysis*, 3rd ed., McGraw--Hill, 1979.

[4] J. B. Conway, *Functions of One Complex Variable I*, 2nd ed., Springer, 1978.

[5] E. M. Stein and R. Shakarchi, *Complex Analysis*, Princeton University Press, 2003.

[6] R. Remmert, *Theory of Complex Functions*, Springer, 1991.

---

**Cite as:** ProofZoom Entry-0008, *Singularities and residues*, ProofZoom (2026).