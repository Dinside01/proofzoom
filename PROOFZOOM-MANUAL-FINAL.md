# ProofZoom Future Notes and Site Manual

## Purpose
This document is meant to help ensure that ProofZoom can continue to develop and be maintained even if its founder is no longer able to manage day-to-day work. It serves two purposes:

1. A running record of future features, design intentions, and implementation notes;
2. A practical manual for understanding, maintaining, and extending the site.

It should be updated as the site evolves.

---

# Part I. Future Notes and Implementation Register

## A. Core Structural Roadmap
- Expansion of foundational sets inside Zermelo-Fraenkel (ZF) theory.
- Integration of transfinite structural hierarchies including omega multiplication, omega squared, and omega to the power of omega.
- Complete navigation frameworks for addressing classical set-theoretic limits such as the Burali-Forti paradox.
- Construction and scaling principles for the first uncountable ordinal (omega_1).

## B. Discussion Spaces (Planned Framework)
1. Entry Discussion: A dedicated feedback space attached to each essay where peers and readers can offer direct corrections, literature references, and pedagogical suggestions.
2. General Discussion: A broader public forum designed for mathematicians, educators, and students to propose future topics deserving a ProofZoom-style transparent exposition.

---

# Part II. Site Manual
## Overview of the Publication Ecosystem
The ProofZoom platform is designed to deliver a high-density, interactive reading experience. Managing this ecosystem requires producing and posting every essay in two distinct, coordinated formats:

1. **The Web Version (`.md`):** Built using Markdown, this version optimizes browser readability, controls metadata, and drives the site's search engine discoverability.
2. **The PDF Version (`.tex`):** Built using LaTeX, this version generates high-fidelity printable assets and drives our deep-dive callout infrastructure.

Both formats feature structural containers. On the web layout, these manifest as interactive text containers; in the PDF layout, they appear as signature visual "PZoom" box frames. These two versions work together seamlessly via hardcoded, sandboxed absolute hyperlinks to give readers frictionless, two-way zoom navigation.

## E. Editorial Style Guide for ProofZoom Entries

(Original sections preserved)

---

## F. Math Rendering Guidelines (Web Version)

Inline math ($...$) should be short and atomic:
- $z_0$, $f'(z_0)$, $\gamma(t)$

Avoid dense inline expressions such as: $\tilde{\xi}_j \in [r_{j-1}, r_j]$

Instead use display math:

$$
\tilde{\xi}_j \in [r_{j-1}, r_j]
$$

Principle: Inline math names objects. Display math expresses relationships.

---

## G. Entry Templates & Front-Matter Standards

ProofZoom entries exist in two separate formats: a Web Markdown version (.md) for browser readability and search optimization, and a PDF version (.tex) for high-fidelity printing and ProofZoom deep-dive callouts.

### 1. The Web Markdown Format (.md)
Every essay file stored in the _entries/ directory must begin with an explicit YAML front-matter block bounded by triple dashes (---). This block populates the site's automated index cards, search parameters, and PDF download pathways.

Required Web Top-Matter Blueprint:
---
layout: entry
title: "Ordinal Numbers and the Shape of Order"
area: "Foundations"
subarea: "Set Theory"
difficulty: "UG-Upper"
published: 2026-06-30
pdf: "/assets/pdfs/entry-0009/entry-0009-ordinals-part-i.pdf"
---

NOTE ON THE ABSTRACT: The text immediately following the front matter automatically serves as the web abstract. No explicit "abstract:" key is required in the front matter. Keep this to a high-level conceptual overview (1-2 paragraphs).

---

### 2. The PDF Version (.tex)
The PDF version uses a full LaTeX preamble rather than YAML front matter. It relies on the custom proofzoom.sty engine to apply the signature styling, margins, and inline box macros.

\documentclass[11pt]{article}
\usepackage{proofzoom}
\usepackage[margin=1in]{geometry}

\begin{document}

\title{Ordinal Numbers and the Shape of Order \\ \large Part I: Foundations and Representation}
\author{Rubin Thomas}
\date{Published: 2026-06-30}
\maketitle

\begin{abstract}
Cardinal numbers measure size. Ordinal numbers measure order...
\end{abstract}

\section{Two Questions: How Many, and In What Order?}
% Main LaTeX body follows here...
\end{document}

---

## H. Pre-Publish Checklist (ProofZoom Linter)

Before publishing:
1. No dense inline math.
2. Relations placed safely in display math.
3. Visual inspection of spacing constraints.
4. Isolation test for back-links.

---

## I. Publication Workflow & Registration Mappings

When a mathematician submits a LaTeX document with deep-dive callouts resolved in an appendix fragment, staff must execute this formal mapping sequence to make the essay live:

1. Author Draft Verification:
   The author writes locally or drafts on Overleaf. Ensure they ran the pre-publish linter checklist.

2. Abstract Extraction:
   - Staff Action: Copy the plain text from the author's LaTeX "\begin{abstract}" block.
   - Staff Action: Paste this text directly underneath the YAML front-matter closing dashes (---) in the web format file "_entries/entry-00XY-slug.md". This sets up the dynamic webpage abstract snippet.

3. Standalone Asset Isolation:
   - Staff Action: Move the appendix proof text out of the master LaTeX file and isolate it inside a raw fragment file (entry-00XY-z.tex).
   - Staff Action: Set up the standalone single-page wrapper (compile-00XY-z.tex) targeting the correct absolute back-link URL via \pzbaseUrl.

4. Catalog & Navigation Registration:
   - Staff Action: Open "entries/index.md" and append the new entry metadata to the chronological master list so it appears in the public index.
   - Staff Action: Open the matching file inside the "areas/" directory (e.g., areas/foundations.md) and link the new entry to its specific subarea taxonomy card.

5. Compile & Live Deployment:
   - Run the local testing server check (Section N).
   - Switch macro to production domain, commit files, and push to GitHub (Section O).

Principle: Writing is local and modular. Publishing requires explicit navigation mapping.

---

## J. PDF Deep-Dive Architecture (The PZoom Engine)

To maintain a high-density, scale-safe reading experience, ProofZoom essays use a cross-file PDF linking mechanism ("ProofZoom Deep Dives"). This allows readers to click an inline box in a master essay, jump to a standalone single-page sub-proof PDF, and click a link to return exactly where they left off.

To compile and link these components successfully, staff must adhere strictly to the Double-Anchor absolute URL system and the one-page layout constraints detailed below.

### 1. The Global Domain Switch (proofzoom.sty)
The main style file contains a macro named \pzbaseUrl. This acts as the master routing switch for the entire archive. 
- Local Development Testing: Must be active when running a local Jekyll server.
  \newcommand{\pzbaseUrl}{http://127.0.0.1:4000}
- Live GitHub Production: Must be uncommented and configured before pushing changes live.
  % \newcommand{\pzbaseUrl}{https://proofzoom.org}

### 2. The Double-Anchor System (Cross-File Targets)
Because modern web browser PDF engines (like Chrome and Firefox's PDF.js) enforce strict security sandboxing rules, relative paths (e.g., `./entry-0009...pdf`) or links containing escaped hash tokens (`\#` or `\%23`) will cause the browser to completely freeze the click action. 

To ensure web responsiveness, all standalone companion files must use a **fully qualified, hardcoded absolute web URL** pointing directly to the production deliverable, paired with a raw, unescaped `#nameddest=` anchor parameter.

- **The Inbound Hook (Master Essay):** The master PDF embeds targets using the `\hypertarget{body:#2}{}` macro structure (e.g., `body:entry-0009-1`).
- **The Outbound Return Link (Standalone Wrapper):** The wrapper file targets this anchor using a literal, unescaped string:
  \href{https://proofzoom.org/assets/pdfs/entry-0009/entry-0009-ordinals-part-i.pdf#nameddest=body:entry-0009-1}{\textbf{\ensuremath{\blacktriangleleft} Return to Main Text}}

### 3. Layout Control & Page Overflow Prevention
Standalone deep dives are designed to be high-impact, single-page reference documents. 

- Strict Spacing Separation: Never use \vfill to position the return link. If a mathematical proof runs long, \vfill will push the navigation line onto an entirely blank second page. Always use a tight, fixed vertical space:
  \vspace{0.8cm}
- Structural Isolation Rule: Mathematical content files (e.g., entry-0009-1.tex) must contain only pure mathematical text. They must never contain trailing return words or formatting commands. All layout structures, section titles, and back-navigation links belong exclusively in the wrapper compiler file (compile-0009-1.tex).

---

## K. Step-by-Step Blueprint Example (The Entry-00XY Standard)

When creating a new mathematical essay with deep-dive callouts (PZoom boxes), staff must follow this exact three-file structural blueprint. This example uses a fictional placeholder identifier 00XY and topic slug ABC, paired with a sub-proof fragment z.


### 1. The Master Essay File (entry-00XY-ABC.tex)
This is the primary narrative file containing the main development text. It uses the `\pzoom` macro to render an inline box that links out to the deeper subproof PDF. 

⚠️ **CRITICAL STRING MAPPING RULE:** The second argument of the `\pzoom` macro—the file path identifier—must be written as a relative path **without** the manual `.pdf` extension. The custom macro automatically appends `.pdf` under the hood. More importantly, this exact string name determines the target coordinate `body:entry-00XY-z` that your standalone return link looks for.

=========================================================================
File: entries/Entry-0009/entry-0009-ordinals-part-i.tex (Master Essay)
=========================================================================
\documentclass[11pt]{article}
\usepackage{proofzoom}
\usepackage[margin=1in]{geometry}

\begin{document}

\section*{2. Order Type: Forgetting Names, Remembering Positions}
Because the cases are symmetric, we assume without loss of generality 
that \psi(a) <' \phi(a).

We will show that \psi(a) cannot lie in the range of \phi. By analyzing 
the placement of an arbitrary element x \in S relative to a, the strict 
order-preserving properties of our isomorphisms yield that \phi(x) \neq \psi(a) 
for all x.

% Parameter #2 matches the asset name exactly. This creates '\hypertarget{body:entry-0009-1}{}'
► \pzoom[Goal={Prove that \psi(a) escapes the image of \phi}]{entry-0009-1}{%
    So \psi(a) \notin im(\phi). This directly contradicts the fact that \phi 
    is a surjective order-isomorphism onto S'.
}

\end{document}


### 2. The Math Fragment File Prototype (entry-0009-1.tex)
This file houses only raw mathematical prose and proofs. To maintain structural modularity, it must never contain layout configuration syntax, headers, or document boundaries.

=========================================================================
File: entries/Entry-0009/entry-0009-1.tex (Pure Math Fragment)
=========================================================================
Because $\phi$ is an order-isomorphism mapping $S$ onto $S'$, it must preserve strict inequalities. We verify that for any arbitrary element $x \in S$:

\begin{itemize}
    \item If $x < a$, the definition of $a$ as the minimal point of disagreement forces $\phi(x) = \psi(x)$. By the strict order-preserving property of $\psi$, since $x < a$, it follows that $\psi(x) <' \psi(a)$. Substituting the equality yields $\phi(x) <' \psi(a)$. Thus, $\phi(x) \neq \psi(a)$.
    \item If $x = a$, then by assumption, $\psi(a) <' \phi(a)$. Thus, $\phi(a) \neq \psi(a)$.
    \item If $x > a$, then since $\psi$ is an order-isomorphism, $\psi(a) <' \psi(x)$. Since $a$ is the point of disagreement where $\psi(a) <' \phi(a)$, transitivity of the strict total order $<'$ on $S'$ yields $\psi(a) <' \phi(a) <' \phi(x)$. Thus, $\psi(a) <' \phi(x)$, meaning $\phi(x) \neq \psi(a)$.
\end{itemize}

Since $x$ was arbitrary, $\phi(x) \neq \psi(a)$ holds globally, showing that $\psi(a)$ escapes the image of $\phi$.


### 3. The Standalone Wrapper File Prototype (compile-0009-1.tex)
This file handles document geometry, formatting, and the standalone sandbox-compliant return navigation. It reads the separate math snippet and links directly back to the production URL coordinate.

=========================================================================
File: entries/Entry-0009/compile-0009-1.tex (Standalone PDF Compiler)
=========================================================================
\documentclass[11pt]{article}
\usepackage[margin=1in]{geometry}
\usepackage{../../proofzoom} % Dynamically pulls the master ProofZoom styles and branding

\hypersetup{hidelinks} % Keeps text clean while preserving interactive metadata

\begin{document}
\pagestyle{empty} % Strips headers/footers for a clean look

\textbf{[PZoom Deep Dive 9.1] Prove that $\psi(a)$ escapes the image of $\phi$}

% =====================================================================================
% CONTENT SOURCE:
% This inputs the raw mathematical proof snippet. Do not duplicate proof text here; 
% all structural edits to the math content should happen inside entry-0009-1.tex.
% =====================================================================================
\input{entry-0009-1.tex} 

\vspace{0.8cm} % Tight fixed space prevents rendering an accidental second blank page
\noindent
% =====================================================================================
% TECHNICAL MAINTENANCE NOTE FOR RETURN LINKS:
% To bypass modern web browser PDF viewer security sandboxes, this link must use an 
% absolute production web URL instead of a relative local file path. 
% 
% The '#nameddest=body:entry-0009-X' fragment is strictly required so that browser 
% PDF engines know exactly which target \hypertarget{body:entry-0009-X} to snap back to 
% inside the main document. Do not escape the hash character (\#) here, as it breaks the URL string.
% =====================================================================================
\href{https://proofzoom.org/assets/pdfs/entry-0009/entry-0009-ordinals-part-i.pdf#nameddest=body:entry-0009-1}{\textbf{\ensuremath{\blacktriangleleft} Return to Main Text}}

\end{document}

---

## L. Deployment & Local Server Testing Protocol

### 1. File Path Architecture on the Server
Compiled PDFs must be organized precisely within your local repository folder structure before launching the server:
- Master Essay PDF: assets/pdfs/entry-00XY/entry-00XY-ABC.pdf
- Standalone Sub-Proof PDF: assets/pdfs/entry-00XY/entry-00XY-z.pdf

### 2. Local Verification Checklist
Before pushing to production, staff must verify the following loop on their local machine:
1. Ensure \newcommand{\pzbaseUrl}{http://127.0.0.1:4000} is the active line in proofzoom.sty.
2. Fire up your local Jekyll/development server (bundle exec jekyll serve).
3. Open a browser and navigate to the master essay file layout.
4. Test the Inbound Link: Click the green PZoom title bar inside the master essay PDF. The browser should open a new tab directly to entry-00XY-z.pdf.
5. Test the Outbound Back-Link: Scroll to the bottom of the sub-proof page and click ◀ Return to Main Text. The browser must snap back to the exact location of the macro box in the master essay without resetting your scroll height to the top of the page.

---

## M. Repository Storage Blueprint & Local Backups

To ensure that mathematical source code is preserved and version-controlled via Git alongside our web text, staff must mirror our Overleaf folder structure inside the local repository's entries/ directory.

### 1. Comprehensive Directory Tree Blueprint

proofzoom-repository/
├── _entries/                              <-- [Live Web Markdown Folder]
│   ├── entry-0001-natural-numbers.md      <-- Controls Entry-0001 webpage & metadata
│   └── entry-0009-ordinals-part-i.md      <-- Controls Entry-0009 webpage & metadata
│
├── entries/                               <-- [Local Backup Workspace for LaTeX]
│   ├── index.md                           <-- The website's public entries catalog page
│   │
│   ├── Entry-0001/                        <-- Unified folder for Essay #1 LaTeX sources
│   │   ├── entry-0001-natural-numbers.tex <-- Master LaTeX essay source file
│   │   ├── entry-0001-1.tex               <-- Pure math fragments (1 through 5)
│   │   └── compile-0001-1.tex             <-- Standalone deep-dive wrapper compilers
│   │
│   └── Entry-0009/                        <-- Unified folder for Essay #9 LaTeX sources
│       ├── entry-0009-ordinals-part-i.tex <-- Master LaTeX essay source file
│       ├── entry-0009-1.tex               <-- Pure math fragments (1 through 5)
│       ├── entry-0009-2.tex
│       ├── compile-0009-1.tex             <-- Standalone deep-dive wrapper compilers
│       └── compile-0009-2.tex
│
├── assets/                                <-- [Production Binary Deliverables]
│   └── pdfs/
│       ├── entry-0001/                    <-- Target directory for Essay #1 compiled PDFs
│       │   ├── entry-0001-natural-numbers.pdf
│       │   └── entry-0001-1.pdf
│       │
│       └── entry-0009/                    <-- Target directory for Essay #9 compiled PDFs
│           ├── entry-0009-ordinals-part-i.pdf
│           ├── entry-0009-1.pdf            <-- Compiled wrappers renamed to match fragments
│           └── entry-0009-2.pdf
│
└── proofzoom.sty                          <-- Core Shared Macro Style Package Engine


### 2. Guardrails for Local Backups

- The Local Backups Rule: Whenever you finish editing or compiling an entry in Overleaf, download the raw source files (.tex and .sty) and copy them into their respective folder inside entries/ (e.g., entries/Entry-0009/). 
- The Static Asset Target: Only the compiled .pdf files belong in the assets/pdfs/ directory. This is the explicit location the web browser hits when executing cross-file hyperlinks via \pzbaseUrl.
- The _site/ Generation Warning: Never copy files directly into _site/. This folder is cleared and generated dynamically by Jekyll during compilation. Always modify the baseline assets/ directory instead.
- The Git Principle: Storing both the web code (_entries/) and the math sources (entries/) in the same root repository guarantees that if the site ever needs to be rebuilt or migrated, a single developer has the complete workspace on their machine.

---

## N. Local Server Verification Protocol

Before pushing any file updates or newly compiled PDFs to the public repository, staff must run a local verification cycle to ensure that no hyperlink anchors are broken.

1. Set the Local Routing Switch:
   Open "proofzoom.sty" and verify that the local development line is active:
   \newcommand{\pzbaseUrl}{http://127.0.0.1:4000}

2. Launch the Development Server:
   Open your local terminal in the root directory of the repository and execute:
   bundle exec jekyll serve

3. Open the Local Index:
   In your web browser, navigate to the local server address:
   http://127.0.0.1:4000/entries/

4. Execute the Deep-Dive Quality Test:
   - Navigate to the essay you are testing (e.g., Entry-0009).
   - Click the "View PDF" link to open the master essay document.
   - Scroll to a callout box and click the green "PZoom" title bar. The browser must open the single-page sub-proof PDF in a new tab.
   - Scroll to the bottom of the sub-proof PDF and click the "◀ Return to Main Text" link. 
   - CRITICAL REQUIREMENT: The browser must snap back to the exact vertical scroll position of the master essay callout box. If it reloads to the top of page 1, the absolute anchor string or the math macro target is broken.

---

## O. Production Deployment Workflow (Pushing to GitHub)

Once local testing passes perfectly, follow this sequence to deploy the updates live to GitHub Pages. Failure to follow this sequence will result in broken live links!

1. Flip the Global Production Switch:
   Open "proofzoom.sty" and comment out the local server string, then uncomment the live domain string:
   % \newcommand{\pzbaseUrl}{http://127.0.0.1:4000}
   \newcommand{\pzbaseUrl}{https://proofzoom.org}

2. Recompile the Workspace Packages:
   If you made changes to "proofzoom.sty", ensure those changes are saved and synced.

3. Stage the Source and Asset Files via Git:
   Open your terminal and check your modified files:
   git status

   Stage the new Markdown web essays, the updated local LaTeX source backups, and the compiled binary PDFs:
   git add _entries/
   git add entries/
   git add assets/pdfs/

4. Commit and Push:
   Commit the changes with a clear descriptive message and push to the remote server:
   git commit -m "Deploy entry-0009 deep dive absolute routing corrections"
   git push origin main

5. Live Production Sanity Check:
   Wait 2-3 minutes for the GitHub Actions automated build runner to complete. Then, visit the live production URL at https://proofzoom.org/entries/ and re-run the deep-dive link cycle to ensure the live anchors resolve correctly across the live domain.

---

## P. The Day-One Technical Lead Smoke Test

This section is a diagnostic checklist for a new technical lead or incoming staff member to verify their local engineering environment matches production within 5 minutes of cloning the repository.

1. The Local Pipeline Verification:
   - Step 1: Open a terminal in the root repository folder and run:
     bundle exec jekyll serve
   - Step 2: Open a browser and verify http://127.0.0.1:4000/entries/ loads cleanly.
   - Step 3: Navigate to the web essay for Entry-0001 or Entry-0009. Verify the front-matter metadata reads correctly and the abstract paragraph matches the master layout.

2. The Compilation Loop Check:
   - Step 1: Open the local backup folder "entries/Entry-0009/" or your active Overleaf project workspace.
   - Step 2: Make a minor dummy text change inside a sub-proof fragment (e.g., entry-0009-3.tex).
   - Step 3: Compile the wrapper file "compile-0009-3.tex" to generate the standalone PDF deliverable.
   - Step 4: Download and rename that PDF to "entry-0009-3.pdf", then drop it into the local folder "assets/pdfs/entry-0009/".
   - Step 5: Click through the green PZoom title bar on the master essay PDF to verify that your new change is instantly visible and that the "◀ Return to Main Text" back-link snaps your browser focus cleanly to the precise structural origin point.

3. Handover Protocol for First Hire:
   - When bringing on your first junior staff member, do not let them push code on day one. Have them execute this exact smoke test locally using Entry-0001 as their training sandbox. Once they can successfully break a link locally, fix it using a standalone wrapper, and trace the double-anchor hash execution in their browser console, they are officially certified to touch production assets.

---

## Q. Manuscript Structural Parsing & Appendix Fragmentation

When an external mathematician submits a LaTeX manuscript with technical edge cases or dense derivations resolved in an appendix, staff must manually parse and break the file apart. Leaving an appendix intact at the end of a master essay violates the high-density layout model of the platform.

### 1. The Division Rule
- The Master Document: Must contain only the high-level conceptual narrative, definitions, main theorem statements, and intuitive proof sketches.
- The Fragment File: Every individual appendix section, theorem lemma, or distinct case-by-case derivation must be extracted into its own clean, isolated source file inside the "entries/Entry-00XY/" directory (e.g., entry-00XY-1.tex).

### 2. Stripping Non-Mathematical Boilerplate
When extracting text into a sub-proof math fragment (entry-00XY-z.tex), staff must strip away all structural wrappers. 
- DO NOT include \documentclass, \begin{document}, \maketitle, or bibliographies.
- DO NOT include section headers like \section{Proof of Theorem 2} or back-navigation links inside the fragment itself.
- DO begin the file immediately with raw mathematical prose (e.g., Let \alpha be a transitive set...).

### 3. The Wrapper Synthesis
For every math fragment extracted, staff must generate a matching wrapper compiler file (compile-00XY-z.tex) following the template in Section K. This wrapper file is the ONLY place where the single-page layout geometry is applied, the custom \section*{} header is declared, and the absolute \href back-link target is injected.

---

# Part III. Infrastructure & System Administration

## R. Local Machine Engineering Requirements

Before a developer or staff member can execute the local testing workflows (Section N), their local machine must be configured with the specific compiler pipelines used by ProofZoom.

### 1. The Core Software Stack
The successor team must ensure the hired developer installs the following prerequisites:
* **Ruby (Version 3.0+):** The underlying programming language that executes the static site builder.
* **Bundler (Ruby Gem):** The dependency manager that fetches the specific software packages for the site.
* **Jekyll (Version 4.0+):** The static site generator engine that transforms our Markdown files (`_entries/`) into web assets.

### 2. Initial Machine Setup Command Sequence
Once Ruby is installed on a new machine, the developer must run this explicit sequence inside a terminal at the root of the repository to match the production environment:

```bash
# Install the bundler package manager
gem install bundler

# Fetch and install all matching site dependencies listed in the Gemfile
bundle install

# Launch the secure local test server
bundle exec jekyll serve

## S. Hosting, Server Access, & Project Credentials

To take over administrative control, deploy updates, or manage site domains, the successor team must have access to three core external platforms. 

⚠️ **SECURITY WARNING:** To prevent unauthorized repository modification or domain hijacking, raw passwords must never be written directly into this document. All operational credentials (usernames, passwords, and two-factor authentication recovery keys) are stored securely in our team's central vault.

### 1. Core Infrastructure Accounts
* **GitHub (`github.com`):** Holds the master production repository. Access is required to execute `git push` operations (Section O) and manage automated GitHub Actions web deployment runners.
* **Domain Registrar ('bigrock.in'):** Controls the `proofzoom.org` domain registration and DNS routing records.
* **Overleaf (`overleaf.com`):** Houses the active LaTeX cloud project workspace where master files, pure math fragments, and compiler wrappers are collaboratively drafted.

### 2. How to Retrieve Access Credentials
* **Credential Location:** Contact Uday Shankar (udaysubashshankar@gmail.com) or Tejo Madhavarappu (tejovrush@gmail.com).
* **Primary GitHub Username:** `Dinside01`
* **Primary GitHub Password:** See Credential Location.
* **URL Registrar Access:** Contact Dr. Pat Prodanovich (pprodano@gmail.com) or Praveena Madhavarapu (praveena.madhavarapu@gmail.com).