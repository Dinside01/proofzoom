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
Because standard web browsers struggle to resolve relative folder links containing specific anchor hashes (#), all cross-file navigation must use absolute paths evaluated through \pzbaseUrl.

- The Inbound Hook (Master Essay): Inside proofzoom.sty, the \pzoom macro engine automatically places a hidden, trackable landing target immediately above the visual callout box using:
  \hypertarget{body:#2}{}
  Example: For Box 9.1, this bakes a target named body:entry-0009-1 into the master PDF.
- The Outbound Return Link (Standalone Wrapper): Every standalone compilation wrapper (e.g., compile-0009-1.tex) must reference this target using a fully qualified absolute macro path at the bottom of the file:
  \href{\pzbaseUrl/assets/pdfs/entry-0009/entry-0009-ordinals-part-i.pdf#body:entry-0009-1}{\textbf{\ensuremath{\blacktriangleleft} Return to Main Text}}

### 3. Layout Control & Page Overflow Prevention
Standalone deep dives are designed to be high-impact, single-page reference documents. 

- Strict Spacing Separation: Never use \vfill to position the return link. If a mathematical proof runs long, \vfill will push the navigation line onto an entirely blank second page. Always use a tight, fixed vertical space:
  \vspace{0.8cm}
- Structural Isolation Rule: Mathematical content files (e.g., entry-0009-1.tex) must contain only pure mathematical text. They must never contain trailing return words or formatting commands. All layout structures, section titles, and back-navigation links belong exclusively in the wrapper compiler file (compile-0009-1.tex).

---

## K. Step-by-Step Blueprint Example (The Entry-00XY Standard)

When creating a new mathematical essay with deep-dive callouts, staff must follow this exact three-file structural blueprint. This example uses a fictional placeholder identifier 00XY and topic slug ABC, paired with a sub-proof fragment z.

### 1. The Master Essay File (entry-00XY-ABC.tex)
This is the primary narrative file containing the main development text. It uses the \pzoom macro to render an inline box that links out to the deeper sub-proof PDF.

=========================================================================
File: entry-00XY-ABC.tex (Master Essay)
=========================================================================
\documentclass[11pt]{article}
\usepackage{proofzoom}
\usepackage[margin=1in]{geometry}

\begin{document}

\section*{1. Main Development Section}
Here is the high-level narrative where we introduce a profound theorem. 
We state the core observation here, but the granular edge-cases are 
offloaded to prevent breaking the reader's conceptual flow.

% The macro parameter #2 must match the sub-proof file name exactly!
► \pzoom[Goal={Verify the edge-case proof elements}]{entry-00XY-z}{%
    This is the high-level summary sentence that remains perfectly visible 
    inline within the main essay text.
}

\end{document}


### 2. The Math Fragment File (entry-00XY-z.tex)
This file contains only raw mathematical text. It must never contain \documentclass, \begin{document}, headers, or navigation links.

=========================================================================
File: entry-00XY-z.tex (Pure Math Fragment)
=========================================================================
Let $x \in S$. We analyze the boundary behavior of our function:
\begin{itemize}
    \item \textbf{Case 1:} If $x < a$, the relation holds trivially by minimality.
    \item \textbf{Case 2:} If $x = a$, the boundary condition is met directly.
\end{itemize}
Therefore, the claim is verified across all cases.


### 3. The Standalone Wrapper File (compile-00XY-z.tex)
This file wraps around the raw math fragment to build the standalone single-page deep dive PDF. It forces a clean layout and injects the absolute back-link URL.

=========================================================================
File: compile-00XY-z.tex (Standalone PDF Compiler)
=========================================================================
\documentclass[11pt]{article}
\usepackage{proofzoom}
\hypersetup{hidelinks}
\usepackage[margin=1in]{geometry}

\begin{document}
\pagestyle{empty} % Strips headers/footers for a clean look

\section*{[PZoom Deep Dive 00XY.z] Detailed Proof Segment}
\input{entry-00XY-z.tex} % Dynamically pulls in your raw math text!

\vspace{0.8cm} % Tight fixed space prevents rendering an accidental second blank page
\noindent
\href{\pzbaseUrl/assets/pdfs/entry-00XY/entry-00XY-ABC.pdf#body:entry-00XY-z}{\textbf{\ensuremath{\blacktriangleleft} Return to Main Text}}

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