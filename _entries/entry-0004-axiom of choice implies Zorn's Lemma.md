---
layout: entry
title: "Axiom of Choice implies Zorn's Lemma"
entry_id: entry-0004
primary_area: foundations
primary_subarea: set-theory
difficulty: UG-Upper

published: 2026-03-28
updated:

permalink: /entries/entry-0004-axiom-of-choice-implies-zorns-lemma/

pdf: /assets/pdfs/entry-0004-axiom-of-choice-implies-zorns-lemma.pdf

abstract: "We present a proof of Zorn’s Lemma based on Lewin’s notion of a conforming set. The proof constructs chains recursively using a choice function and shows that all such constructions are forced to agree on their initial segments. Their union therefore forms a single maximal construction, which the choice function paradoxically compels to extend further, yielding a contradiction."
---

## 1. Introduction

**Theorem 1.1 (Zorn's Lemma).**  
Let \((X,\le)\) be a nonempty partially ordered set in which every chain has an upper bound. Then \(X\) has a maximal element.

---

## 2. Setup

Assume, for contradiction, that \((X,\le)\) has no maximal element. Then every chain has a *strict* upper bound. (If \(C\) is a chain in \(X\), then by choosing an upper bound \(u\) of \(C\) and then choosing an element \(x\) so that \(x>u\), we obtain an element \(x\in X\) such that \(y<x\) for every \(y\in C\). Such an element will be called a *strict upper bound* of \(C\).)

By the Axiom of Choice, fix a function that assigns to every chain in \(X\), a strict upper bound \(f(C)\):
\[
f:\{\text{chains in }X\} \to X
\]
such that
\[
c < f(C) \quad \text{for all } c \in C.
\]

---

## 3. Central Idea

Instead of building one maximal chain directly, we construct all possible chains using a choice function and show they are forced to agree on their initial segments. Their union is therefore a single well-defined maximal construction, which the choice function paradoxically forces to extend. A maximal construction that cannot stop must contradict itself. At its core, the argument constructs a maximal object by forcing all possible constructions to agree, and then shows that the assumption of no maximal element compels this object to extend further.

---

## 4. Definitions

For \(A \subseteq X\) and \(x \in A\), define
\[
I(A,x) = \{y \in A : y < x\}.
\]

By the Axiom of Choice, fix once and for all a function
\[
f : \{\text{chains in } X\} \to X
\]
such that \(c < f(C)\) for every \(c \in C\).

A subset \(A \subseteq X\) is called *conforming* if:
- (a) \(A\) is well-ordered,
- (b) \(x = f(I(A,x))\) for every \(x \in A\).

---

**Interpretation.**  
The function \(f\) is fixed in advance and is not chosen to fit \(A\). Rather, a conforming set is one that conforms to the behavior of the choice function \(f\). \(A\) evolves according to \(f\): each element \(x \in A\) is exactly the element selected by \(f\) from the set of all earlier elements \(I(A,x)\) it had selected. The assumption that \((X,\le)\) has no maximal element ensures that \(f(C)\) is strictly greater than every element of \(C\), so each stage of the construction strictly extends the previous ones.

In the parent set \(X\), there is a next element, say \(x_4\), since every chain has a strict upper bound. However, \(f(C)\) need not be \(x_4\). Suppose instead that \(f(C) = y\), where \(y\) is a strict upper bound. Then \(x_1 < x_2 < x_3 < y\) is a new chain, and \(y = f(I(A,y))\). Thus \(A\) is built step-by-step by the choice function \(f\). It need not contain every element of a chain in \(X\), but only those selected by \(f\). In particular, not every chain in \((X,\le)\) is conforming, but some are.

As example, consider a chain \(C\) which is \(x_1<x_2<x_3\). In the parent set \(X\), there is a next element, say \(x_4\), of \(C\) because every chain has a strict upper bound as seen above. But \(f(C)\) may not be \(x_4\). Suppose \(f(C)=y\), where \(y\) is a strict upper bound. Then \(x_1<x_2<x_3<y\) is a new chain and \(f(I(A,y))=y\). \(A\) is thus the chain built by \(f\) step by step from a chain of \((X,\le)\). \(A\) does not contain every element of the chain in \((X,\le)\) that \(A\) is built from. \(A\) has only the elements produced by the choice function \(f\). Thus, not every chain in \((X,\le)\) is conforming, but some chains are.

Since \(A\) is well-ordered, each \(I(A,x)\) is a chain in \(X\), so \(f(I(A,x))\) is well-defined.

---

**Remark (Construction viewpoint).**  
Conforming sets may be built inductively: starting with \(x_0 = f(\varnothing)\), then
\[
x_1 = f(\{x_0\}), \quad x_2 = f(\{x_0,x_1\}), \quad \dots
\]
and continuing transfinitely. A conforming set is precisely a set that arises from such a construction (possibly stopped at some stage).

Condition (b) encodes this entire recursive process: it forces every element of \(A\) to appear exactly when dictated by \(f\).

## 5. Comparability of Conforming Sets (Comparability Lemma)

**Guiding idea.**  
Each conforming set is generated step-by-step by the same choice function \(f\). Thus two such constructions cannot diverge: once they agree on an initial segment, the next element is uniquely determined because the function has already chosen that.

---

**Lemma 5.1.**  
If \(A\) and \(B\) are conforming subsets of \(X\) and \(A \neq B\), then one of these sets is an initial segment of the other.

---

**Proof.**

Recall that \(A\) and \(B\) are well-ordered and satisfy
\[
x = f(I(A,x)) \quad \text{for all } x \in A,
\qquad
x = f(I(B,x)) \quad \text{for all } x \in B.
\]

---

Define
\[
C = \{\, x \in A \cap B : I(A,x) = I(B,x) \,\}.
\]

---

\(C \ne \varnothing\), for if \(a\) and \(b\) are, respectively, the least elements of \(A\) and \(B\), then, since \(I(A,a)=I(B,b)=\varnothing\), \(a=f(\varnothing)=b\), and hence \(a=b \in C\).

---

**Claim.** \(C\) is an initial segment of both \(A\) and \(B\).

Let \(x \in C\) and let \(u \in A\) with \(u < x\).  
We show that \(u \in C\), proving that \(C\) is an initial segment of \(A\).

Since \(u < x\) and \(x \in C\), we have
\[
u \in I(A,x) = I(B,x),
\]
so \(u \in B\).

We now prove
\[
I(A,u) = I(B,u).
\]

Let \(v \in I(A,u)\). Then \(v < u < x\), so \(v \in I(A,x)=I(B,x)\), hence \(v \in B\) and \(v<u\), so \(v \in I(B,u)\). Thus
\[
I(A,u) \subseteq I(B,u).
\]

The reverse inclusion follows by symmetry, so
\[
I(A,u) = I(B,u).
\]

Thus \(u \in C\).

---

This shows that every element of \(A\) below \(x\) lies in \(C\), so \(C\) is an initial segment of \(A\).  
The same argument applies to \(B\). Thus \(C\) is an initial segment of both \(A\) and \(B\), proving the claim.

---

If both \(A \setminus C\) and \(B \setminus C\) are nonempty, we compare the first points at which the two constructions \(A\) and \(B\) diverge. Define
\[
a = \min(A \setminus C), \qquad b = \min(B \setminus C).
\]

---

**Claim.** \(I(A,a)=I(B,b)=C\).

We prove
\[
I(A,a) = C.
\]

First, let \(u \in I(A,a)\). Then \(u \in A\) and \(u < a\). Since \(a = \min(A \setminus C)\), there is no element of \(A \setminus C\) smaller than \(a\). Thus every element of \(A\) below \(a\) must lie in \(C\). So \(u \in C\).  
Hence
\[
I(A,a) \subseteq C.
\]

Conversely, let \(u \in C\). We show \(u < a\).

- If \(u = a\), this contradicts \(a \notin C\).
- If \(a < u\), then since \(u \in C\) and \(C\) is an initial segment of \(A\), every element of \(A\) below \(u\) lies in \(C\). But \(a \in A\) and \(a < u\), so \(a \in C\), contradiction.

Thus \(u < a\), so \(u \in I(A,a)\), and hence
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

---

Since \(A\) and \(B\) are conforming,
\[
a = f(I(A,a)) = f(C),
\qquad
b = f(I(B,b)) = f(C).
\]

Thus
\[
a = b.
\]

Let \(c = a = b\). Then \(c \in A\) and \(c \in B\).

Also,
\[
I(A,c) = I(B,c) = C,
\]

Since \(c \in A \cap B\) and \(I(A,c) = I(B,c) = C\), by definition of \(C\) we have \(c \in C\).  
But \(c = a \in A \setminus C\), contradiction.

---

Therefore at least one of \(A \setminus C\) or \(B \setminus C\) is empty.  
Thus either \(A = C\) or \(B = C\); so one is an initial segment of the other. □

## 6. The union \(U\) of all conforming subsets of \(X\)

**Lemma 6.1.**  
The union \(U\) of all conforming subsets of \(X\) is conforming.

---

**Proof.**

We first show that \(U\) is a chain. Let \(x,y \in U\). There are conforming sets \(A_x\) and \(A_y\) such that \(x \in A_x\) and \(y \in A_y\). The Comparability Lemma implies that one of these sets is a subset of the other, so without loss of generality suppose that \(A_x \subseteq A_y\). Then \(x,y \in A_y\), and \(A_y\) is a chain, so either \(x \leq y\), or \(y \leq x\).

---

Now we show that \(U\) is well-ordered by \(\leq\). The key point is that all conforming sets are comparable by initial segments, so the union behaves like a single well-ordered construction rather than a disjoint aggregation. Suppose that \(\emptyset \neq S \subseteq U\); we want to show that \(S\) has a least element under \(\leq\). Fix \(s \in S\). Choose a conforming set \(A\) with \(s \in A\). \(A\) is well-ordered by \(\leq\), so let
\[
a = \min \{x \in A \cap S : x \leq s\};
\]
we claim that \(a = \min S\). Let \(x \in S\); if \(x \in A\), then certainly \(a \leq x\), so suppose that \(x \in S \setminus A\). There is some conforming \(A_x\) such that \(x \in A_x\). Since \(x \notin A\), we have \(A_x \not\subset A\). By the Comparability Lemma, one of \(A_x\) and \(A\) is an initial segment of the other. Since \(A_x\) is not a subset of \(A\), it follows that \(A\) is an initial segment of \(A_x\). Since also \(x \in A_x \setminus A\) and \(a \in A\), we have \(a < x\) in this case as well; hence \(a = \min S\).

---

It remains to show that if \(x \in U\), then \(x = f(I(U,x))\). Let \(x \in U\); there is a conforming set \(A_x\) such that \(x \in A_x\). By definition \(x = f(I(A_x,x))\), so we’re done if we can show that \(f(I(U,x)) = f(I(A_x,x))\). It suffices to show that \(I(U,x) = I(A_x,x)\). Since \(A_x \subset U\), \(I(A_x,x) \subseteq I(U,x)\). So we need only show that \(I(U,x) \subseteq I(A_x,x)\).

So suppose \(y \in I(U,x)\). That is, \(y \in U\) and \(y < x\). Since \(U\) is the union of all conforming subsets of \(X\), there is a conforming set \(A_y\) such that \(y \in A_y\). Then, \(A_x\) and \(A_y\) being conforming sets, one of them is an initial segment of the other.

If \(A_y\) is an initial segment of \(A_x\), then \(y \in A_y \subseteq A_x\). Thus \(y \in A_x\) and \(y < x\), so \(y \in I(A_x,x)\).

On the other hand, if \(A_x\) is an initial segment of \(A_y\), then \(A_x \subseteq A_y\). Since \(y \in A_y\) and \(y < x\), and \(A_x\) is an initial segment of \(A_y\), every element of \(A_y\) below \(x\) must lie in \(A_x\). Thus \(y \in A_x\), proving that \(I(U,x) \subseteq I(A_x,x)\).

□

---

**Guiding idea.**  
By Lemma 5.1, all conforming sets agree on their initial segments. Thus they are not independent constructions but compatible stages of a single transfinite process governed by \(f\). Their union \(U\) therefore represents the maximal such construction obtained by extending this process as far as possible. This is possible precisely because all conforming sets agree on their initial segments, so no incompatibility arises in forming the union.

## 7. Proof of Zorn's Lemma

**Proof.**

Suppose \(X\) has no maximal element. Since \(U\) is a conforming subset of \(X\), there exists \(f(U)\) so that 
\[
u < f(U) \quad \text{for all } u \in U.
\]

So \(f(U) \notin U\). Thus the construction \(U\), which aggregates all possible conforming constructions, is still not maximal: the choice function forces it to extend further. Let \(U^* = U \cup \{f(U)\}\).

---

**Insight. \(U^*\) is conforming:**

\(U^*\) is well-ordered since \(U\) is well-ordered and \(f(U)\) lies above all elements of \(U\).

For \(x \in U\), \(x = f(I(U,x)) = f(I(U^*,x))\).

For \(f(U)\):
\[
I(U^*, f(U)) = U,
\]
so
\[
f(U) = f(I(U^*, f(U))).
\]

---

Now \(U\) is the union of all conforming subsets of \(X\). Since \(U^*\) is conforming, it must be contained in \(U\). Thus \(f(U) \in U\), contradicting that \(f(U)\) is strictly greater than every element of \(U\). □

---

**Reader Takeaway.**  
A conforming set grows by repeatedly applying the fixed choice function, so each stage is forced by what came before. Because all such constructions agree on initial segments, their union \(U\) forms a single maximal construction. But the choice function then forces \(U\) itself to extend, yielding a contradiction—so a maximal element must exist.

---


## 8. Conceptual Summary

A conforming set is a transfinite construction governed by the choice function:
\[
x_\alpha = f(\{x_\beta : \beta < \alpha\}).
\]

The Comparability Lemma shows that all such constructions are compatible (they agree on initial segments), so their union forms a maximal transfinite construction.

---

## 9. Toward the Equivalence of AC, Zorn’s Lemma, and Well-Ordering

The argument above is more than a proof of Zorn’s Lemma from the Axiom of Choice: it reveals a general structural principle underlying several fundamental results in set theory.

The key feature is that a global object is built by extending partial constructions step-by-step, with the Axiom of Choice ensuring that each extension is possible. The compatibility of these constructions guarantees that they assemble into a single coherent structure.

From this perspective, the Axiom of Choice provides the mechanism that allows such a construction to continue at every stage, producing a single coherent object obtained by consistently extending partial constructions as far as possible. The Comparability Lemma shows that all such possible constructions agree on their initial segments, so they fit together into a single coherent object. The union \(U\) may therefore be viewed as the result of a maximal transfinite construction.

Zorn’s Lemma can thus be understood as a principle asserting that such recursively built structures must reach a maximal stage. The contradiction arises because the choice function forces any such maximal construction to extend further.

This viewpoint forms one side of a well-known equivalence:
\[
\text{Axiom of Choice} \;\Longleftrightarrow\; \text{Zorn’s Lemma} \;\Longleftrightarrow\; \text{Well-Ordering Theorem}.
\]

In the reverse direction, Zorn’s Lemma can be used to show that every set admits a well-ordering, and from this one can recover the Axiom of Choice. The essential idea is again the same: one organizes partial constructions (such as partial well-orderings) into a poset and uses maximality to obtain a global object.

Thus these three principles are not isolated results but different expressions of a single underlying idea:

> **Global structure emerges from consistent local choices.**

---

## References

- K. Kuratowski, *Sur une caractérisation des alephs*, Fundamenta Mathematicae, 1922.  
- M. Zorn, *A remark on method in transfinite algebra*, Bulletin of the American Mathematical Society, 41 (1935), 667–670.  
- J. Lewin, *A simple proof of Zorn’s Lemma*, American Mathematical Monthly, April 1991.  
- T. Jech, *The Axiom of Choice*, North-Holland, 1973.

---

**Cite as:** ProofZoom Entry-0004, *Axiom of Choice implies Zorn's Lemma*, ProofZoom (2026).