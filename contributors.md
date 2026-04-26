---
layout: page
title: Contributors
permalink: /contributors/
---

## ProofZoom Entry Template

See the **[ProofZoom Entry Template](/contributors/template/)** for the
recommended structure of entries and the LaTeX template used for
ProofZoom essays.

---

## Contributors

ProofZoom welcomes contributions from mathematicians who share the goal of making the **central ideas behind important proofs visible to mathematicians outside the specialty**.

Entries should emphasize conceptual clarity while presenting proofs with enough intermediate steps to make the logical derivation completely clear.

ProofZoom serves as **a conceptual guide to important mathematical proofs**.

---

## Mission

**ProofZoom aims to make the central idea behind a proof visible to mathematicians outside the specialty and to include intermediate steps where necessary so that the derivation of the proof is clear.**

Mathematical papers often present proofs in full technical detail, but the conceptual mechanism driving the argument may not be immediately visible to readers outside the field. ProofZoom entries aim to reveal that mechanism clearly while presenting proofs in a logically transparent way.

---

## Structure of an Entry

### Central Idea

Explain the **key conceptual insight of the result** and its **relevance within the subject area**, including connections to major results in the theory.

### Proof Idea

Describe the **mechanism that makes the proof work**. The reader should be able to understand why the theorem is true before encountering the full technical details.

### Proof

Present the **rigorous mathematical proof**, including intermediate steps where necessary so that the logical derivation is clear.

---

## Style Guidelines

Entries should aim for:

- conceptual clarity  
- concise exposition  
- precise mathematics  
- clear logical derivations  

Whenever possible:

- emphasize ideas before calculations  
- include diagrams when they clarify structure  
- highlight the mechanism behind the proof  
- include intermediate steps when they help illuminate the argument  

---

## Technical Guidelines for Preparing Entries

To ensure that entries render correctly on the ProofZoom website, contributors should observe the following technical requirements.

### File Format
- Files must be saved as `.md`
- Encoding: UTF-8
- The file must begin exactly with:

    ---

(No blank line before it.)

---

### YAML Front Matter
- Copy the header from a working entry
- Modify only necessary fields
- Ensure both opening and closing `---` are present

---

### Math Rendering
- Inline math: `$...$`
- Display math: `$$...$$`
- Avoid `\(...\)` and `\[...\]`

---

### Filenames and Links
- Use consistent naming: `entry-000X-topic-name.md`
- PDF filename must match the `.md` filename

---

### Local Testing

After adding an entry, run:

    rmdir /s /q _site
    bundle exec jekyll serve

Then verify:

    dir _site\entries

Correct output:

    entry-000X-topic-name   <DIR>

Incorrect output:

    entry-000X-topic-name.md

---

### Common Pitfalls

- Blank line before `---` → entry not rendered  
- Incorrect encoding → front matter ignored  
- Filename mismatch → broken links  
- Math not rendering → check delimiters and layout  

---

### Git Workflow

    git status
    git add .
    git commit -m "Add Entry-000X"
    git pull --rebase origin main
    git push origin main

---

## Audience

ProofZoom is written for **mathematicians**, but not necessarily specialists in the topic.

An entry should ideally be understandable by a graduate-level mathematician working in a different area.

---

## Length

Entries should focus on a single concept or theorem. Most entries will typically range from **3–8 pages**.

---

## Citation Format

Each entry should include a citation line such as:

**Cite as:**  
ProofZoom Entry-XXXX, *Title*, ProofZoom (Year).

---

## Guiding Principle

**Show the idea first, and make the proof steps clear.**

---

## Pre-Publish Checklist

Before pushing an entry to ProofZoom, verify the following:

- [ ] The file begins exactly with `---` (no blank line before it)  
- [ ] The file is saved as `.md` with UTF-8 encoding  
- [ ] YAML front matter matches a working entry  
- [ ] Inline math uses `$...$` and display math uses `$$...$$`  
- [ ] Filenames and PDF paths are consistent  
- [ ] The entry renders correctly on the local server  
- [ ] `_site/entries` shows the entry as a **directory**, not a `.md` file  
- [ ] All links (especially the PDF link) work  
- [ ] The entry appears correctly in the Entries list  
- [ ] No unintended files are included in `git status`  

**Final step:**

    git add .
    git commit -m "Add Entry-XXXX"
    git pull --rebase origin main
    git push origin main