---
layout: entry
title: "Axiom of Choice implies Zorn's Lemma"
entry_id: entry-0004
primary_area: Foundations
primary_subarea: Set-theory
permalink: /entries/entry-0004-axiom-of-choice-implies-zorns-lemma/

pdf: /assets/pdfs/entry-0004-axiom-of-choice-implies-zorns-lemma.pdf

abstract: "We prove Zorn’s Lemma from the Axiom of Choice via conforming sets. The method constructs all possible chains, shows their compatibility, and produces a maximal construction whose forced extension yields a contradiction—revealing the mechanism behind maximality."

difficulty: UG-Upper
published: 2026-03-28
updated:
---

## Introduction

**Theorem (Zorn's Lemma).**  
Let $(X,\le)$ be a nonempty partially ordered set in which every chain has an upper bound. Then $X$ has a maximal element.

---
## Setup

Assume, for contradiction, that $X$ has no maximal element.

Then every chain has a *strict* upper bound. (If $C$ is a chain in $X$, then by choosing an upper bound $u$ of $C$ and then choosing an element $x$ so that $x>u$, we obtain an element $x\in X$ such that $y<x$ for every $y\in C$. Such an element will be called a *strict upper bound* of $C$.)

By the Axiom of Choice, fix a function that assigns to every chain in $C$, a strict upper bound $f(C)$:
$$
f:\{\text{chains in }X\} \to X
$$
such that
$$
c < f(C) \quad \text{for all } c \in C.
$$

---

## Central Idea

Instead of building one maximal chain directly, we construct all possible chains using a choice function and show they are forced to agree on their initial segments. Their union is therefore a single well-defined maximal construction, which the choice function paradoxically forces to extend.

---

## Definitions

For $A \subseteq X$ and $x \in A$, define
$$
I(A,x) = \{y \in A : y < x\}.
$$

A subset $A \subseteq X$ is *conforming* if:

(a) $A$ is well-ordered,

(b) $x = f(I(A,x))$ for every $x \in A$.


## Comparability of Conforming Sets (Comparability Lemma)

**Lemma.**  
If $A$ and $B$ are conforming subsets of $X$ and $A\neq B$, then one of these sets is an initial segment of the other.

**Proof.**

Recall that $A$ and $B$ are well-ordered and satisfy
\[
x = f(I(A,x)) \quad \text{for all } x \in A,
\qquad
x = f(I(B,x)) \quad \text{for all } x \in B.
\]

Define
\[
C = \{\, x \in A \cap B : I(A,x) = I(B,x) \,\}.
\]

$C\ne\varnothing$, for if $a$ and $b$ are, respectively, the least elements of $A$ and $B$, then, since $I(A,a)=I(B,b)=\varnothing$, $a=f(\varnothing)=b$,  and hence $a=b\in C$.

**Claim.** $C$ is an initial segment of both $A$ and $B$.

Let $x \in C$ and let $u \in A$ with $u < x$.  
We show that $u \in C$, proving that $C$ is an initial segment of $A$.

Since $u < x$ and $x \in C$, we have
\[
u \in I(A,x) = I(B,x),
\]
so $u \in B$.

We now prove
\[
I(A,u) = I(B,u).
\]

Let $v \in I(A,u)$. Then $v < u < x$, so $v \in I(A,x)=I(B,x)$, hence $v \in B$ and $v<u$, so $v \in I(B,u)$. Thus
\[
I(A,u) \subseteq I(B,u).
\]

The reverse inclusion follows by symmetry, so
\[
I(A,u) = I(B,u).
\]

Thus $u \in C$.

This shows that every element of $A$ below $x$ lies in $C$, so $C$ is an initial segment of $A$. The same argument applies to $B$. Thus $C$ is an initial segment of both $A$ and $B$, proving the claim.

If both $A \setminus C$ and $B \setminus C$ are nonempty, we compare the first points at which the two constructions $A$ and $B$ diverge. Define
\[
a = \min(A \setminus C), \qquad b = \min(B \setminus C).
\]

**Claim.** $I(A,a)=I(B,b)=C.$

We prove
\[
I(A,a) = C.
\]

First, let $u \in I(A,a)$. Then $u \in A$ and $u < a$. Since $a = \min(A \setminus C)$, there is no element of $A\setminus C$ smaller than $a$. Thus every element of $A$ below $a$ must lie in $C$. So $u \in C$.  
Hence
\[
I(A,a) \subseteq C.
\]

Conversely, let $u \in C$. We show $u < a$.

- If $u = a$, this contradicts $a \notin C$.
- If $a < u$, then since $u \in C$ and $C$ is an initial segment of $A$, every element of $A$ below $u$ lies in $C$. But $a \in A$ and $a < u$, so $a \in C$, contradiction.

Thus $u < a$, so $u \in I(A,a)$, and hence
\[
C \subseteq I(A,a).
\]

Therefore
\[
I(A,a) = C.
\]

Similarly,
\[
I(B,b) = C.
\]
This proves the claim.

Since $A$ and $B$ are conforming,
\[
a = f(I(A,a)) = f(C),
\qquad
b = f(I(B,b)) = f(C).
\]

Thus
\[
a = b.
\]

Let $c = a = b$. Then $c \in A$ and $c \in B$.

Also,
\[
I(A,c) = I(B,c) = C,
\]
Since $c \in A\cap B$ and $I(A,c) = I(B,c) = C$, by definition of $C$ we have $c \in C$. But $c = a \in A \setminus C$, contradiction.

Therefore at least one of $A \setminus C$ or $B \setminus C$ is empty.  
Thus either $A = C$ or $B = C$; so one is an initial segment of the other.

## Construction of the Maximal Conforming Set

Let $\mathcal{C}$ be the collection of all conforming subsets of $X$.

By the Comparability Lemma, $\mathcal{C}$ is totally ordered by inclusion.

Define
\[
M = \bigcup_{A \in \mathcal{C}} A.
\]

We show that $M$ is conforming.

First, we show that $M$ is totally ordered.

Let $x,y \in M$. Then $x \in A$ and $y \in B$ for some $A,B \in \mathcal{C}$. Since $\mathcal{C}$ is totally ordered by inclusion, either $A \subseteq B$ or $B \subseteq A$. In either case, $x$ and $y$ lie in a common conforming set, and hence are comparable.

Next, we show that $M$ is well-ordered.

Let $S \subseteq M$, $S \ne \varnothing$. We must show that $S$ has a least element.

Since $S \subseteq M$, for each $x \in S$ there exists $A_x \in \mathcal{C}$ such that $x \in A_x$.

The family $\{A_x : x \in S\}$ is totally ordered by inclusion. Let $A \in \mathcal{C}$ be one of these sets which contains some element of $S$ and is maximal among them.

Then $S \cap A \ne \varnothing$. Since $A$ is well-ordered, $S \cap A$ has a least element, say $m$.

We claim that $m$ is the least element of $S$.

Let $y \in S$. Then $y \in B$ for some $B \in \mathcal{C}$. Since $\mathcal{C}$ is totally ordered, either $A \subseteq B$ or $B \subseteq A$.

If $B \subseteq A$, then $y \in A$, so $y \in S \cap A$, and hence $m \le y$.

If $A \subseteq B$, then $m \in A \subseteq B$, and since $B$ is well-ordered and $y \in B$, we have $m \le y$.

Thus $m$ is the least element of $S$.

Next, let $x \in M$. Then $x \in A$ for some $A \in \mathcal{C}$. Since $A$ is conforming,
\[
x = f(I(A,x)).
\]

We show that
\[
I(M,x) = I(A,x).
\]

Let $y \in I(M,x)$. Then $y \in M$ and $y < x$. Thus $y \in B$ for some $B \in \mathcal{C}$. Since $x \in A$ and $\mathcal{C}$ is totally ordered, either $B \subseteq A$ or $A \subseteq B$. In either case, $y \in A$. Thus $y \in I(A,x)$, so
\[
I(M,x) \subseteq I(A,x).
\]

Conversely, if $y \in I(A,x)$, then $y \in A \subseteq M$ and $y < x$, so $y \in I(M,x)$. Hence
\[
I(A,x) \subseteq I(M,x).
\]

Therefore
\[
I(M,x) = I(A,x),
\]
and hence
\[
x = f(I(M,x)).
\]

Thus $M$ is conforming.

## Completion of the Proof

Since $M$ is conforming, it is well-ordered and satisfies
\[
x = f(I(M,x)) \quad \text{for all } x \in M.
\]

Since $M$ is a chain in $X$, it has a strict upper bound $f(M)$.

We claim that $M \cup \{f(M)\}$ is conforming.

First, $M \cup \{f(M)\}$ is well-ordered, since $f(M)$ is greater than every element of $M$.

Next, for $x \in M$, we have
\[
I(M \cup \{f(M)\}, x) = I(M,x),
\]
and hence
\[
x = f(I(M,x)) = f(I(M \cup \{f(M)\}, x)).
\]

Finally,
\[
I(M \cup \{f(M)\}, f(M)) = M,
\]
and hence
\[
f(M) = f(I(M \cup \{f(M)\}, f(M))).
\]

Thus $M \cup \{f(M)\}$ is conforming.

This contradicts the definition of $M$ as the union of all conforming sets.

Therefore $X$ has a maximal element.

## Conceptual Summary

The proof proceeds by constructing all conforming sets simultaneously and showing that they are comparable by inclusion.

The union $M$ of all conforming sets is therefore well-defined and inherits the conforming property.

The key idea is that the use of the choice function forces every step of the construction, so that any two constructions must agree on their common initial segment.

Thus all constructions are compatible and fit together into a single maximal construction.

The final step shows that this maximal construction can still be extended, yielding a contradiction.


## Bridge to the Axiom of Choice and Well-Ordering
The argument above is more than a proof of Zorn’s Lemma from the Axiom of Choice: it reveals a general structural principle underlying several fundamental results in set theory.

The key feature is that a global object is built by extending partial constructions step-by-step, with the Axiom of Choice ensuring that each extension is possible. The compatibility of these constructions guarantees that they assemble into a single coherent structure.

From this perspective, the Axiom of Choice provides the mechanism that allows such a construction to continue at every stage. The result is a single coherent object obtained by consistently extending partial constructions as far as possible. The Comparability Lemma shows that all possible such constructions agree on their initial segments, so they fit together into a single coherent object. The union $M$ may therefore be viewed as the result of a maximal transfinite construction.

Zorn’s Lemma can thus be understood as a principle asserting that such recursively built structures must reach a maximal stage. The contradiction arises because the choice function forces any such maximal construction to extend further.

This viewpoint forms one side of a well-known equivalence:
\[
\text{Axiom of Choice} \;\Longleftrightarrow\; \text{Zorn’s Lemma} \;\Longleftrightarrow\; \text{Well-Ordering Theorem}.
\]

In the reverse direction, Zorn’s Lemma can be used to show that every set admits a well-ordering, and from this one can recover the Axiom of Choice. The essential idea is again the same: one organizes partial constructions (such as partial well-orderings) into a poset and uses maximality to obtain a global object.

Thus these three principles are not isolated results but different expressions of a single underlying idea:

> Global structure can be obtained from consistent local choices.

## References

- K. Kuratowski, *Sur une caractérisation des alephs*, Fundamenta Mathematicae, 1922.

- M. Zorn, *A remark on method in transfinite algebra*, Bulletin of the American Mathematical Society, 41 (1935), 667–670.

- J. Lewin, *A simple proof of Zorn’s Lemma*, American Mathematical Monthly, April 1991.

- T. Jech, *The Axiom of Choice*, North-Holland, 1973.


---

**Cite as.** ProofZoom Entry-0004: *Axiom of Choice implies Zorn's Lemma* (published 2026-03-28).