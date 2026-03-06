# ProofZoom Future Notes and Site Manual

## Purpose
This document is meant to help ensure that ProofZoom can continue to develop and be maintained even if its founder is no longer able to manage day-to-day work. It serves two purposes:

1. a running record of future features, design intentions, and implementation notes;
2. a practical manual for understanding, maintaining, and extending the site.

It should be updated as the site evolves.

---

# Part I. Future Notes and Implementation Register

## 1. What this section is for
This section is a living notebook of features, improvements, and architectural intentions that should be preserved for future maintainers.

Each note should answer four questions:
- What is the idea?
- Why does it matter?
- What files or systems would likely be involved?
- What is a plausible implementation path?

## 2. Suggested name for this section
Recommended title:

**ProofZoom Future Notes and Implementation Register**

Alternative titles:
- ProofZoom Development Notes
- ProofZoom Continuity Notes
- ProofZoom Future Roadmap

## 3. Suggested entry format
Each future note can use the following template.

### Item
**Title:**

**Status:** proposed / planned / in progress / implemented / deferred

**Purpose:**

**Why it matters:**

**Likely files involved:**

**Implementation outline:**
1.
2.
3.

**Notes for future maintainers:**

**Date added:**

**Last updated:**

## 4. Initial future items to record

### Item 1
**Title:** Entry-specific discussion space

**Status:** planned

**Purpose:**
Allow mathematicians, students, and readers to comment on a particular entry.

**Why it matters:**
This creates a scholarly feedback loop. Corrections, clarifications, references, and alternate viewpoints can improve entries over time.

**Likely files involved:**
- `_layouts/entry.html`
- possibly a future `/community/` or discussion integration
- stylesheet files
- moderation documentation

**Implementation outline:**
1. Decide whether discussion is handled by a third-party system or a custom ProofZoom workflow.
2. Add an entry-specific discussion link or embedded discussion block.
3. Create moderation and editorial rules.
4. Decide how accepted corrections affect the canonical essay.

**Notes for future maintainers:**
Keep entry-specific discussion separate from general topic proposals.

**Date added:** 2026-03-06

**Last updated:** 2026-03-06

### Item 2
**Title:** General topic proposal space

**Status:** planned

**Purpose:**
Provide a place where mathematicians and students can suggest topics that deserve a ProofZoom entry.

**Why it matters:**
This helps the site grow in response to real needs.

**Likely files involved:**
- future `/community/`, `/proposals/`, or similar page
- navigation and layout files
- moderation documentation

**Implementation outline:**
1. Create a dedicated page for proposals.
2. Distinguish requests for new entries from comments on existing entries.
3. Establish editorial criteria for selecting proposals.

**Notes for future maintainers:**
This should remain distinct from essay-linked discussion.

**Date added:** 2026-03-06

**Last updated:** 2026-03-06

### Item 3
**Title:** Previous / next entry navigation

**Status:** proposed

**Purpose:**
Allow visitors to browse entries more naturally.

**Why it matters:**
This makes ProofZoom feel like a coherent mathematical reference work rather than isolated pages.

**Likely files involved:**
- `_layouts/entry.html`
- collection ordering logic

**Implementation outline:**
1. Determine ordering rule, likely by `entry_id`.
2. Add previous/next navigation block near the bottom of entry pages.
3. Test on the first several entries.

**Date added:** 2026-03-06

**Last updated:** 2026-03-06

### Item 4
**Title:** Richer `/entries/` page presentation

**Status:** proposed

**Purpose:**
Improve the entries index so that it functions like a true library catalogue.

**Why it matters:**
As the number of entries grows, discoverability will matter more.

**Likely files involved:**
- `entries/index.md`
- `_layouts/entries.html`
- stylesheet files

**Implementation outline:**
1. Display title, entry number, abstract, and taxonomy cleanly.
2. Consider filters by area and subarea.
3. Add optional search later.

**Date added:** 2026-03-06

**Last updated:** 2026-03-06

---

# Part II. Site Manual

## A. Architecture Manual

### 1. Purpose
This section explains how ProofZoom is organized and how the main files and folders work together.

### 2. Core idea of the site
ProofZoom is a static site built around structured mathematical entries. The site uses a collection-based architecture so that essays can be added consistently and automatically surfaced throughout the site.

### 3. Key folders and files

#### `_config.yml`
The main Jekyll configuration file.

Typical responsibilities:
- site title and base settings;
- permalink behavior;
- declaration of collections such as `_entries`.

#### `_entries/`
The collection containing the entry files.

Each file in this folder represents one ProofZoom entry and typically includes front matter such as:
- `entry_id`
- `title`
- `primary_area`
- `primary_subarea`
- `abstract`
- `authors`
- `updated`
- `pdf`

#### `entries/index.md`
The page declaration for `/entries/`.

This file should remain minimal. It does not contain the listing logic itself. Instead, it points to the layout that renders the entries index.

#### `_layouts/entries.html`
The layout used to generate the `/entries/` page.

Typical responsibilities:
- reading the `_entries` collection through `site.entries`;
- sorting entries;
- rendering the list or cards for all entries.

#### `_layouts/entry.html`
The layout for an individual entry page.

Typical responsibilities:
- rendering title and metadata;
- showing abstract and citation information;
- rendering the entry body;
- showing PDF links and footer elements;
- providing a placeholder or future space for discussion.

#### `areas/`
Area pages such as Foundations, Algebra, Geometry, and others.

These pages organize the site at a higher level and can eventually guide readers to relevant entries by subject.

#### `_layouts/area.html`
The layout used for area pages.

#### `assets/` or stylesheet files
These control visual presentation, typography, spacing, and card styling.

#### `_data/`
Optional structured data for reusable site-wide content, such as sponsor details.

### 4. Architectural principle
Keep content, metadata, and layout responsibilities separated:
- entry files contain the mathematical content and front matter;
- layouts control how content is rendered;
- config defines global behavior;
- data files store reusable structured information.

This separation makes the site easier to maintain over time.

---

## B. Maintenance Manual

### 1. Purpose
This section explains how to maintain the site locally and publish changes to GitHub.

### 2. Local repository and GitHub repository
ProofZoom has:
- a local site folder on the computer;
- a GitHub repository that stores the published source;
- a deployed GitHub Pages site.

### 3. Basic maintenance workflow
A typical update cycle is:
1. edit files locally;
2. preview locally if needed;
3. check what changed with Git;
4. commit the changes;
5. push the changes to GitHub;
6. verify that GitHub Pages publishes the new version correctly.

### 4. Basic Git commands
Typical commands:

```bash
git status
git add .
git commit -m "Describe the change"
git pull --rebase origin main
git push origin main
```

### 5. Safe editing practice
Before major structural changes:
- make a backup copy of the local folder;
- commit working versions before experimental edits;
- change one architectural component at a time.

### 6. When pushing fails
Common causes include:
- local branch behind GitHub;
- merge or rebase conflicts;
- incomplete commit state.

Basic recovery pattern:
1. run `git status`;
2. if needed, run `git pull --rebase origin main`;
3. resolve any conflict;
4. continue the rebase;
5. push again.

### 7. Publishing responsibility
After a push, check the public site and confirm:
- the intended page loads;
- links are correct;
- styles render properly;
- collection pages show expected entries.

### 8. Maintenance advice for future stewards
A future maintainer should preserve:
- the restrained mathematical design of the site;
- the collection-driven architecture;
- consistency of front matter across entries;
- clarity and editorial seriousness.

### 9. Recommended future additions to this manual
This manual should later include:
- local preview instructions;
- branch and backup policy;
- naming conventions for entries;
- style conventions for metadata;
- publication checklist for new entries;
- editorial workflow for revisions and errata;
- sponsor and citation handling;
- instructions for transferring stewardship to another maintainer.

---

## C. Entry Front‑Matter Specification

To ensure that all ProofZoom entries are rendered correctly and can be indexed automatically by the site, each entry file in the `_entries/` collection should follow a consistent front‑matter structure.

### Required fields

**`entry_id`**  
A unique identifier for the entry, typically of the form `entry-0001`, `entry-0002`, etc.  
This identifier is used for ordering and citation.

**`title`**  
The full title of the entry.

**`primary_area`**  
The major mathematical area to which the entry belongs (for example `foundations`, `analysis`, `algebra`, `geometry`).

**`primary_subarea`**  
A more specific classification within the area.

### Recommended fields

**`abstract`**  
A short paragraph describing the purpose and content of the entry.

**`authors`**  
The author or authors of the entry. This may appear as

```
authors: "Rubin Thomas"
```

or

```
authors:
  - "Rubin Thomas"
  - "ChatGPT"
```

or

```
authors:
  - name: "Rubin Thomas"
    role: "author"
```

**`updated`**  
Date of the most recent revision.

**`difficulty`**  
An approximate level such as `UG‑Lower`, `UG‑Upper`, or `Graduate`.

**`tags`**  
Keywords that help categorize the entry.

**`pdf`**  
Optional link to a downloadable PDF version of the entry.

### Example entry front matter

```
---
layout: entry
entry_id: entry-0001
title: "Natural Numbers as the Smallest Inductive Structure"
primary_area: foundations
primary_subarea: natural-numbers
abstract: "A structural introduction to the natural numbers as the smallest inductive set."
authors:
  - "Rubin Thomas"
updated: 2026-02-28
difficulty: UG-Lower
tags:
  - natural-numbers
  - induction
---
```

Maintaining consistent front matter ensures that entries automatically appear correctly in

- the `/entries/` index
- area pages
- citation blocks

Future maintainers should preserve this structure when adding new entries.

---

## D. Publishing a New Entry — Step‑by‑Step

This section outlines the recommended workflow for adding a new ProofZoom entry.

### 1. Write the entry
Prepare the exposition using the ProofZoom style of clear and structured explanation.

### 2. Create the entry file
Create a new file in the `_entries/` folder.

The filename should follow the pattern:

```
entry-XXXX-descriptive-slug.md
```

Example:

```
entry-0003-induction-and-well-ordering.md
```

### 3. Add the required front matter
At the top of the file include the standard metadata block:

```
---
layout: entry
entry_id: entry-0003
title: "Induction and the Well-Ordering Principle"
primary_area: foundations
primary_subarea: induction
abstract: "An exposition explaining the equivalence of induction and well-ordering."
authors:
  - "Rubin Thomas"
updated: 2026-03-06
difficulty: UG-Lower
---
```

### 4. Write the body of the entry
Below the front matter place the essay content. Mathematical notation may be written using LaTeX.

### 5. Verify site integration
After saving the file, confirm that:

- the entry appears automatically on the `/entries/` page;
- the citation block renders correctly;
- metadata such as area and difficulty appear properly.

### 6. Commit the change
From the repository root run:

```
git add .
git commit -m "Add entry XXXX: short description"
```

### 7. Synchronize with GitHub
Before pushing, update from the remote repository:

```
git pull --rebase origin main
```

### 8. Push the new entry

```
git push origin main
```

### 9. Verify the published site
After the push completes, confirm that the entry appears correctly on the live site.

---

## E. Editorial Style Guide for ProofZoom Entries

ProofZoom entries aim to present mathematics with clarity, structural transparency, and pedagogical care. Authors contributing entries should follow these editorial principles.

### 1. Clarity of reasoning
Arguments should make the logical flow of ideas visible. When a derivation step relies on a non‑obvious inference, the reasoning connecting the steps should be explained.

### 2. Structural exposition
Whenever possible, an entry should make the structure of the argument visible. Useful techniques include:

- stating definitions clearly before they are used;
- separating lemmas and propositions from surrounding narrative;
- explaining the role of a result within the broader topic.

### 3. Motivation
Where appropriate, provide brief explanations of *why* a concept or result is important within the subject area.

### 4. Concision without omission
Exposition should remain concise but should avoid omitting reasoning that is essential for understanding the argument.

### 5. Mathematical tone
The style should remain mathematically precise while also being readable for advanced students. Avoid unnecessary informal language but aim for clarity rather than excessive formalism.

### 6. Diagrams and examples
When diagrams or examples substantially improve understanding, they should be included.

### 7. Citations and attribution
If an entry closely follows a classical exposition or proof, the original source should be acknowledged in the references or discussion.

---

## F. Repository Structure Diagram

The following simplified diagram shows the principal structure of the ProofZoom repository.

```
Proofzoom/
│
├─ _config.yml
├─ README.md
├─ PROOFZOOM-MANUAL.md
│
├─ _entries/        ← mathematical essays
├─ _layouts/        ← page templates used by Jekyll
├─ entries/         ← entries index page
├─ areas/           ← pages for major mathematical areas
├─ assets/          ← stylesheets and site resources
└─ _data/           ← optional structured site data
```

This structure separates responsibilities clearly:

- **content** lives in `_entries/`
- **presentation logic** lives in `_layouts/`
- **index pages** live in folders such as `entries/` and `areas/`
- **styles and resources** live in `assets/`

Maintaining this separation helps keep the site easy to understand and maintain.

---

# Part III. Stewardship and Continuity

## Why this matters
ProofZoom should be understandable and maintainable by someone other than its founder. For that reason, the project should preserve not only files, but also institutional memory.

## Continuity principle
A future steward should be able to answer three questions from this document:
1. What is ProofZoom trying to be?
2. How is the site organized?
3. How does one safely maintain and extend it?

## Suggested future documents
Over time, this master document may be split into:
- `FUTURE-NOTES.md`
- `SITE-MANUAL.md`
- `EDITORIAL-GUIDE.md`
- `MAINTENANCE-CHECKLIST.md`

For now, keeping everything in one place is reasonable.

