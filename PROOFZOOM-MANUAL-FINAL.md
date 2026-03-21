# ProofZoom Future Notes and Site Manual

## Purpose
This document is meant to help ensure that ProofZoom can continue to develop and be maintained even if its founder is no longer able to manage day-to-day work. It serves two purposes:

1. a running record of future features, design intentions, and implementation notes;
2. a practical manual for understanding, maintaining, and extending the site.

It should be updated as the site evolves.

---

# Part I. Future Notes and Implementation Register

(Original content preserved)

---

# Part II. Site Manual

## E. Editorial Style Guide for ProofZoom Entries

(Original sections preserved)

---

## F. Math Rendering Guidelines (Web Version)

Inline math ($...$) should be short and atomic:
- $z_0$, $f'(z_0)$, $\gamma(t)$

Avoid dense inline expressions such as:
$\tilde{\xi}_j \in [r_{j-1}, r_j]$

Instead use display math:

$$
\tilde{\xi}_j \in [r_{j-1}, r_j]
$$

Principle:
Inline math names objects.
Display math expresses relationships.

---

## G. Entry Template (Web Version)

Each entry should follow:

1. Overview
2. Key Idea
3. Main Development
4. Theorem / Proof
5. Interpretation
6. References

---

## H. Pre-Publish Checklist (ProofZoom Linter)

Before publishing:

1. No dense inline math
2. Relations in display math
3. Visual inspection
4. Isolation test if needed

---

## I. Publication Workflow

1. Author writes locally
2. Run checklist
3. Submit for review
4. Editor approves
5. Merge → publish

Principle:
Writing is local. Publishing is controlled.

---

# Part III. Stewardship and Continuity

(Original content preserved)
