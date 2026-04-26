---
layout: entry
title: "Zorn's Lemma, Well-Ordering, and the Axiom of Choice"
entry_id: entry-0007
primary_area: Foundations
primary_subarea: Set Theory
difficulty: UG-Upper
published: 2026-04-24
updated:

permalink: /entries/entry-0007-zornslemma-wellordering-axiomofchoice/

pdf: /assets/pdfs/entry-0007-zornslemma-wellordering-axiomofchoice.pdf
abstract: "We prove that Zorn’s Lemma implies the Well-Ordering Theorem, and show how a well-ordering yields the Axiom of Choice. The proof constructs a well-ordering by extending partial well-orderings to a maximal one, which must include every element of the set. Once such a global order is available, each set in a family acquires a canonical choice as its least element. Together with the converse implication, this establishes the equivalence of the Axiom of Choice, Zorn’s Lemma, and the Well-Ordering Theorem, revealing a common principle underlying selection, maximality, and order."

---

## 1. Introduction

The Axiom of Choice, Zorn’s Lemma, and the Well-Ordering Theorem are among the most important principles in modern mathematics. Although they appear to express very different ideas, it is a fundamental fact that they are logically equivalent.

The Axiom of Choice asserts the existence of selections from arbitrary collections of nonempty sets. Zorn’s Lemma guarantees the existence of maximal elements in partially ordered sets under suitable hypotheses. The Well-Ordering Theorem states that every set can be arranged in a linear order in which every nonempty subset has a least element. Each of these principles captures a different way of organizing infinite collections: through selection, through maximality, and through order.

Historically, the equivalence of these principles emerged gradually. Ernst Zermelo first introduced the Axiom of Choice in 1904 in order to prove that every set can be well ordered. Three decades later, Max Zorn formulated what is now known as Zorn’s Lemma, providing a powerful and flexible tool that is widely used across mathematics.

In this entry, we present the implication from Zorn’s Lemma to the Well-Ordering Theorem, followed by the deduction of the Axiom of Choice from the existence of well-orderings. Together with the converse implication already established in a previous entry, this completes the equivalence of the three principles.

The proof that Zorn’s Lemma implies the Well-Ordering Theorem proceeds by considering the collection of all well-ordered subsets of a given set and extending them as far as possible. The central idea is that a maximal well-ordered subset must in fact include every element of the set. Once a well-ordering is obtained, the Axiom of Choice follows naturally: one simply selects, from each set in a family, its least element with respect to a single global well-ordering.

Thus, what begins as a question about maximal elements leads to a global ordering of arbitrary sets, and ultimately to the ability to make consistent selections across infinite collections.

---

## 2. Zorn's Lemma implies the Well-Ordering Theorem

**Theorem 2.1.** Every set can be well ordered.

*Idea of proof.* 
The proof rests on a single principle: a well-order can be extended without altering what has already been ordered.

We consider all well-ordered subsets of $X$, ordered by inclusion as initial segments. Two kinds of extension are possible. First, given a chain of such subsets, their union carries a natural well-order because all the orders agree on overlaps. Second, if a well-ordered subset does not yet contain all elements of $X$, one can adjoin a new element and place it strictly above all existing elements, extending the order without disturbing previous comparisons.

Zorn’s Lemma guarantees the existence of a maximal well-ordered subset under these extensions. The key point is that maximality forbids any further extension. But the second construction shows that any proper subset can always be extended by adjoining a new element. Therefore, the maximal well-ordered subset must already be the whole set.

Thus, $X$ admits a well-ordering.


**Proof.** Let $X$ be a set. Let
$$
\mathcal{W} = \lbrace(A,R_A): A\in P(X),\quad R_A\subseteq A\times A,\quad R_A \text{ is a well-ordering of } A\rbrace.
$$
$\mathcal{W}\ne \emptyset$ since $(\lbrace x\rbrace, =)\in \mathcal{W}$ for every $x\in X$.

We define a partial order $\preceq$ on $\mathcal{W}$ as follows. For $(A,R_A)$ and $(B,R_B)$ in $\mathcal{W}$,
$$
(A,R_A) \preceq (B,R_B)\iff (A,R_A) \text{ is an initial segment of } (B,R_B)
$$
which is to say that
- $A \subseteq B$,
- $R_B\cap (A\times A)=R_A$ (that is, the two orderings $R_B$ and $R_A$ agree on $A$), and
- $A$ is an initial segment of $B$ under $R_B$; that is,
$$
a \in A\text{ and } b \in B\setminus A,\text{ then } aR_B b.
$$
(This is saying that $A$ is an initial segment of $B$ in a well-ordered set $X$ if 
$A=\lbrace x\in B : x\,R_B\, b \text{ for every } b\in B\setminus A\rbrace$.)

Thus, $(A, R_A)$ sits inside $(B, R_B)$ exactly as an initial segment — no new elements appear before those of $A$. Then $\preceq$ is evidently a partial order on $\mathcal{W}$.

**Claim:** Every chain in $\mathcal{W}$ has an upper bound.

Let $C=\lbrace(A_i,R_{A_i})\rbrace_{i \in I}$ be a chain in $(\mathcal{W},\preceq)$.

Since $C$ is totally ordered, the sets $A_i$ are nested by virtue of the definition of $\preceq$. Indeed, if $(A_i,R_{A_i})$ and $(A_j,R_{A_j})$ lie in the chain, then either $(A_i,R_{A_i})\preceq (A_j,R_{A_j})$ or the reverse holds, and hence either $A_i\subseteq A_j$ or $A_j\subseteq A_i$. Let
$$
Y= \bigcup_{i \in I} A_i.
$$

We define a relation $R_Y$ on $Y$ by declaring for $s,t\in Y$:
$$
s R_Y t \quad \text{if and only if} \quad s,t \in A_i \text{ for some } i \text{ and } s R_{A_i} t.
$$

This is well defined, since for $i,j \in I$, the chain condition implies that one of $(A_i,R_{A_i})$ and $(A_j,R_{A_j})$ extends the other, and hence their partial orders agree on their overlap.

We claim that $(Y,R_Y)$ is a well-ordered set.

First, $R_Y$ is a total order. Indeed, if $s,t \in Y$, then $s,t \in A_i$ for some $i$, and hence are comparable under $R_{A_i}$.

Next, let $S \subseteq Y$ be nonempty. Since $S\subseteq Y=\cup A_i$, every element of $S$ lies in some $A_i$, so for at least one index $i$, $S\cap A_i\ne\emptyset.$ Let
$$
u = \text{min}_{R_{A_i}} (S\cap A_i),
$$
where the minimum is with respect to $R_{A_i}$.

*Claim:* $u$ is a minimum for $S$ with respect to $R_Y$.

To prove the claim, let $s$ be an arbitrary element of $S$. Then either $s \in A_i$ or not.

If $s \in A_i$, then $u R_Y s$ follows from $u R_{A_i} s$.

If $s\notin A_i$, then $s\in A_j$ for some $A_j\in C$. Since $C$ is a chain and $s \notin A_i$ but $s \in A_j$, we must have $(A_i, R_{A_i}) \preceq (A_j, R_{A_j})$, so that $u, s \in A_j$. But then $A_j$ being totally ordered (because it is well-ordered) by $R_{A_j}$, we have $uR_{A_j}s$ and hence $uR_Ys$. So $u$ is a minimum for $S$ with respect to $R_Y$, and the claim is proved.

Thus $(Y,R_Y)$ is well-ordered and hence $(Y,R_Y)\in \mathcal{W}$. But $(Y,R_Y)$ is an upper bound of the chain $C$. Since $C$ is an arbitrary chain in $\mathcal{W}$, we conclude that every chain in $\mathcal{W}$ has an upper bound.

By Zorn's lemma, $\mathcal{W}$ has a maximal element, say $(M,\prec)$.

**Claim:** The maximal element is all of $X$.

Suppose $M \ne X$. Let $x \in X \setminus M$.

Define a relation $\prec'$ on $M \cup \lbrace x\rbrace$ by:
- it agrees with $\prec$ on $M$, and  
- for every $a \in M$, $a \prec' x$.

Thus, $\prec'$ extends the order $\prec$ without altering any of its existing comparisons, and places the new element $x$ strictly above all elements of $M$. This is analogous to the construction of upper bounds for chains, where the order is extended while preserving agreement on overlaps.

We claim that $(M \cup \lbrace x\rbrace, \prec')$ is a well-ordered set.

First, $\prec'$ is a total order. If $a, b \in M$, they are comparable under $\prec$. If one of them is $x$, say $a \in M$, then $a \prec' x$ by definition.

Next, let $S \subseteq M \cup \lbrace x\rbrace$ be nonempty. If $x \notin S$, then $S \subseteq M$ and has a least element since 
$(M, \prec)$ is well-ordered.

If $x \in S$, then either $S = \lbrace x\rbrace$, in which case $x$ is least, or $S$ contains an element of $M$. In that case, $S \cap M$ is nonempty and has a least element $m$, and since every element of $M$ precedes $x$, this $m$ precedes every element of $S$, and hence is the least element of $S$.

Thus $(M \cup \lbrace x\rbrace, \prec')$ is well-ordered.

Therefore, by the definition of the partial order $\preceq$ on $\mathcal{W}$, we have

$(M, \prec) \preceq (M \cup \lbrace x\rbrace, \prec')$,

so that $(M, \prec)$ is a proper initial segment of $(M \cup \lbrace x\rbrace, \prec')$ in $\mathcal{W}$, contradicting the maximality of $(M, \prec)$.

Therefore $M = X$, and $\prec$ is a well-ordering of $X$ (the relation $\preceq$ was only an auxiliary order on $\mathcal{W}$, whereas $\prec$ is the induced order on $X$).

---

## 3. Well-Ordering implies the Axiom of Choice

**Theorem 3.1.** The Well-Ordering Theorem implies the Axiom of Choice.

*Idea of proof.*
We well-order the union of the given family of sets, thereby imposing a single global structure on all elements involved. Each set in the family then inherits a least element from this order, yielding a canonical choice from each set.

**Proof.** Let $\lbrace X_i\rbrace_{i \in I}$ be a family of nonempty sets, and let
$$
Y = \bigcup_{i \in I} X_i.
$$
By the Well-Ordering Theorem, the set $Y$ admits a well-ordering, say $\prec$.

For each $i \in I$, since $X_i$ is a nonempty subset of the well-ordered set $(Y, \prec)$, it has a least element with respect to $\prec$. Define a function $f : I \to \bigcup_{i \in I} X_i$ by
$$
f(i) = \text{the least element of } X_i \text{ with respect to } \prec.
$$

Then $f(i) \in X_i$ for every $i \in I$. Hence $f$ is a choice function for the family $\lbrace X_i\rbrace_{i \in I}$.

This establishes the Axiom of Choice.

---

## 4. Closing perspective

The Axiom of Choice, Zorn’s Lemma, and the Well-Ordering Theorem express, in different forms, a single underlying principle.

The Axiom of Choice is a principle of selection: from each set in a family, one may choose an element. Zorn’s Lemma is a principle of maximality: in a partially ordered set where every chain can be extended, there exists an element that cannot be extended further. The Well-Ordering Theorem is a principle of structure: every set admits an ordering in which each subset has a least element.

The arguments in this entry make the connections between these viewpoints explicit. Zorn’s Lemma allows one to extend partial well-orderings until no further extension is possible, and such maximality forces a well-ordering of the entire set. Once such a global order is available, the need for arbitrary choices disappears: each set in a family comes equipped with a distinguished element, namely its least element.

Thus, what begins as a statement about maximal elements leads to a global organization of all elements, and ultimately to a canonical method of selection. The equivalence of these principles reflects a deep unity in the ways mathematics handles infinite collections—through choice, through maximality, and through order.

---

## References

[1] E. Zermelo, *Beweis, dass jede Menge wohlgeordnet werden kann*, Mathematische Annalen, 59 (1904), 514–516.

[2] E. Zermelo, *Untersuchungen über die Grundlagen der Mengenlehre I*, Mathematische Annalen, 65 (1908), 261–281.

[3] M. Zorn, *A remark on method in transfinite algebra*, Bulletin of the AMS, 41 (1935), 667–670.

[4] P. R. Halmos, *Naive Set Theory*, Springer, 1974.

[5] W. Rudin, *Principles of Mathematical Analysis*, 3rd ed., McGraw–Hill, 1976.

[6] T. Jech, *Set Theory*, Springer Monographs in Mathematics, 2003.  
(For a comprehensive treatment of the equivalence of the Axiom of Choice, Zorn’s Lemma, and the Well-Ordering Theorem.)

[7] ProofZoom Entry-0004, *Axiom of Choice implies Zorn’s Lemma*, ProofZoom (2026).

---

**Cite as:** ProofZoom Entry-0007, *Zorn’s Lemma, Well-Ordering, and the Axiom of Choice*, ProofZoom (2026).