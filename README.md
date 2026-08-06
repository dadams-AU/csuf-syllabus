# CSUF LaTeX Syllabus Templates

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

LaTeX syllabus templates for California State University, Fullerton (CSUF) faculty.  
**University-compliant**, **accessible**, and easy to adapt for different courses.

---

## 🚀 Quick Start

### Option 1: Overleaf (Recommended for Beginners)
1. Go to [Overleaf](https://www.overleaf.com/) and create/login to account
2. Upload this entire repository OR clone from GitHub
3. **IMPORTANT:** Menu → Compiler → **LuaLaTeX** (not PDFLaTeX!)
4. Open `csuf_template/csuf_template.tex` 
5. Click **Recompile** (takes 3-15 seconds)
6. Start customizing!

### Option 2: Local Installation (For Advanced Users)
```bash
git clone https://github.com/dadams-AU/csuf-syllabus.git
cd csuf-syllabus/csuf_template
lualatex csuf_template.tex
```

---

## Repository Structure

```
csuf-syllabus/
├── csuf_template/        # 📄 Complete, ready-to-use syllabus template (START HERE)
├── csuf_template_shell/  # 📋 Minimal "shell" template for customization
├── csuf_logo.png         # 🏫 CSUF logo image (required for templates)
├── example/              # 📚 Example syllabus showcasing template usage
├── .gitignore
├── LICENSE
└── README.md
```

---

## Key Features & Why This Matters

- **CSUF branding and logo** - Professional, university-compliant appearance
- **Accessibility-ready** - PDF/UA tagging for screen readers and compliance (this is required!)
- **LuaLaTeX-compatible** - Modern LaTeX with better font handling
- **Built-in structure** - Common syllabus sections already organized
- **Professional typography** - TeX Gyre fonts with fallbacks
- **Works everywhere** - Overleaf, local LaTeX, any editor

---

## For Beginners: Essential Info

**What you need to know:**
- This creates professional PDFs from text files
- Compile time: 3-15 seconds (LuaLaTeX is slower but better)
- The accessibility features are **required** for CSUF compliance
- Start with `csuf_template/` - it has everything you need

**Don't panic if you see errors about:**
- Missing packages (Overleaf handles this automatically)
- Font warnings (fallbacks will work)
- Long compile times on first run (normal for LuaLaTeX)

---

## For Advanced Users: Technical Requirements

### Required Software
- **LuaLaTeX** compiler (XeLaTeX/PDFLaTeX will not work with accessibility tagging)
- **LaTeX distribution** (TeX Live 2023+, MiKTeX, or MacTeX)
- `csuf_logo.png` in the template directory

### Key Packages
- `tagpdf` (for PDF/UA accessibility tagging)
- `pdfmanagement-testphase`
- `fontspec`
- `tex-gyre` font families

### Local Installation Commands

**TeX Live:**
```bash
tlmgr update --self --all
tlmgr install tagpdf tex-gyre tex-gyre-math fontspec
```

**Ubuntu/Debian:**
```bash
sudo apt install texlive-luatex texlive-latex-extra fonts-texgyre
```

**Arch/Manjaro:**
```bash
sudo pacman -S texlive-latexextra texlive-fontsextra
```

**macOS (MacTeX):** Use TeX Live Utility to install `tagpdf` and `tex-gyre`

**Windows (MiKTeX):** Open MiKTeX Console → Settings → enable *Install missing packages on-the-fly*

---

## Troubleshooting Flowchart

```
Compilation fails?
├── Using LuaLaTeX? 
│   ├── No → Switch to LuaLaTeX compiler
│   └── Yes → Continue
├── On Overleaf?
│   ├── Yes → Should work automatically (contact support)
│   └── No → Continue to local troubleshooting
├── Missing tagpdf?
│   ├── Run: tlmgr install tagpdf
│   └── Still failing → Use Overleaf instead
├── Font errors?
│   ├── Run: tlmgr install tex-gyre tex-gyre-math
│   └── Still failing → Template has fallbacks, should still work
└── All else fails → Use Overleaf (seriously, it just works)
```

**Quick verification commands (local only):**
```bash
kpsewhich tagpdf-base.sty
kpsewhich texgyretermes-regular.otf
```

---

## Customization Guide

### Basic Changes (Everyone Should Do This)
1. **Course Information**: Replace all `[COURSE CODE]`, `[COURSE TITLE]`, etc.
2. **Instructor Details**: Update name, email, office hours
3. **Schedule**: Modify the course calendar section
4. **Policies**: Adapt university policies to your specific needs

### Advanced Customization
- Add/remove sections as needed
- Adjust formatting using standard LaTeX commands
- Modify accessibility tagging if needed (advanced users only — but never remove the `testphase` line from `\DocumentMetadata`; see [Verifying Tagging](#verifying-tagging-important))
- Fallbacks ensure compilation even without optimal setup

### Accessible Table Pattern

Use `tabular` (fixed-width columns) or `tabularx` (stretchable `X`/`L` columns) for syllabus tables. Declare the header row to the tagging engine, then style it with `\rowcolor`:

```latex
\tagpdfsetup{table/header-rows={1}}
\begin{tabularx}{\linewidth}{L c c}
\rowcolor{csufTableHeader}
\textbf{Assignment} & \textbf{Weight} & \textbf{Due} \\
...
\end{tabularx}
```

`table/header-rows={1}` is what emits real `<TH>` cells with `/Scope`; the shaded header improves visual scanning without replacing the accessibility tagging. The `L` column type (left-aligned, stretchable) is defined in each template's preamble.

> ⚠️ **Do not use `tabularray` (`tblr`).** Earlier versions of these templates did. Despite its `rowhead = 1` key, tabularray nests `<P>` tags inside table cells, which fails PDF/UA-2 validation (rule Table 5, P-P-1) — while still reporting `Tagged: yes`. This was caught by veraPDF in July 2026 and all templates were converted to `tabular`/`tabularx`.

### Heading Styling — do not use `titlesec`

> ⚠️ **Do not load `titlesec`.** `csuf_template.tex` did until August 2026. titlesec replaces the kernel's sectioning internals, and the tagging engine then never sees the headings: all 16 `\section*` commands were emitted as **ordinary paragraphs**, so the PDF contained **zero heading structure elements**. A screen reader user got no heading navigation through a 13-page syllabus — the single most important way people move around a long document.
>
> This is worse than the tabularray bug in one respect: **veraPDF reports `PASS` on PDF/UA-2 anyway.** PDF/UA does not require headings to *exist*, only that any headings present are correctly nested. Zero headings is vacuously valid. It is nonetheless a **WCAG 1.3.1 (Info and Relationships, Level A)** failure, which is what the ADA Title II rule actually measures against.

Style headings with `\@startsection` instead, which the tagging engine understands:

```latex
\makeatletter
\renewcommand\section{\@startsection{section}{1}{0pt}%
  {-1.2ex plus -.4ex}{0.6ex}%
  {\sffamily\bfseries\Large\addfontfeatures{LetterSpace=2.0}}}
\makeatother
```

This produces visually identical output to the old titlesec setup (verified pixel-for-pixel across all 13 pages; only a ~8px vertical shift on pp. 9–10) while restoring all 16 headings.

**How to check your own file:**

```bash
qpdf --qdf --object-streams=disable yours.pdf - | grep -c "/S /section"
```

If that returns `0` but your syllabus visibly has headings, your headings are not tagged.

---

## Why Accessibility Matters (CSUF Compliance)

The PDF/UA tagging in these templates gives you:
- Screen reader compatibility (headings, lists, table headers, reading order)
- Better searchability
- Most of what an accessibility review will look for

**This isn't optional** - it's required for CSUF syllabi.

### What these templates do *not* by themselves guarantee

The DOJ's ADA Title II rule (89 FR 31320) names **WCAG 2.1 Level AA** as the technical standard, and it covers PDFs posted on a public entity's website. PDF/UA-2 overlaps heavily with WCAG but **is not the same standard**, and a veraPDF `PASS` is not a compliance certificate. PDF/A-4f is archival conformance with *no* accessibility meaning at all — don't let it be cited as evidence.

Verified as passing in these templates: contrast (1.4.3 — all colors ≥ 8:1 on white), image alt text (1.1.1), table headers and heading structure (1.3.1), document language (3.1.1), and descriptive link text (2.4.4).

Still your responsibility in each syllabus you build:
- **2.4.2 Page Titled** — set `pdftitle` in `\hypersetup` to your real course title. A leftover `COURSE TITLE` placeholder is what a screen reader announces on open.
- **1.1.1** — real alt text on any image *you* add.
- **1.3.1** — use `\section`/`\subsection`, not bold text, for anything that reads as a heading.

Two AA criteria that **no** fixed-layout PDF fully satisfies: **1.4.10 Reflow** and **1.4.12 Text Spacing**, both of which assume content can reflow to a narrow viewport and accept user-overridden spacing. The standard mitigation is to post the syllabus as **HTML in Canvas** with the PDF as a supplementary download. A tagged PDF is a good PDF; it is not equivalent to an accessible web page.

**CSUF's compliance deadline is April 26, 2027.** (The rule sets two dates; the other, April 24, 2026, applies to larger public entities.) Syllabi posted to Canvas or a department site are in scope as "conventional electronic documents." There is no exception for documents still in active use — the archived-content exception does not cover a syllabus you are currently teaching from.

---

## Verifying Tagging (Important)

⚠️ A syllabus can compile with **zero errors**, declare PDF/UA conformance in its metadata, and still produce an **untagged** PDF that a screen reader cannot navigate. Nothing in the LaTeX log warns you. Always verify before you post a syllabus.

### Step 1: the one-line check

```bash
pdfinfo csuf_template.pdf | grep Tagged
```

You want `Tagged: yes`. If you get `Tagged: no`, the PDF will fail Canvas **UDOIT** and Adobe Acrobat accessibility review no matter what the metadata claims.

### Step 2: validate against PDF/UA-2 (don't skip this)

⚠️ `Tagged: yes` is necessary but **not sufficient**. It only says a structure tree exists — not that the structure is valid. A file can report `Tagged: yes` and still fail PDF/UA-2 outright; that is exactly what a bad table package does (see [Accessible Table Pattern](#accessible-table-pattern)). Run a real validator:

```bash
verapdf -f ua2 --format text csuf_template.pdf
```

You want `PASS`. On `FAIL`, get the specific rules:

```bash
verapdf -f ua2 --format xml csuf_template.pdf | grep -A2 'status="failed"'
```

veraPDF is free and open source ([verapdf.org](https://verapdf.org/)); on Debian/Ubuntu, `apt install verapdf`. If you can't install it, veraPDF also offers a browser-based validator, and Adobe Acrobat Pro's Accessibility Checker catches many (not all) of the same issues.

### Step 3: validate against PDF/A-4f (archival conformance)

The templates also claim PDF/A, so check that flavour too:

```bash
verapdf -f 4f --format text csuf_template.pdf
```

**Why `4f` and not `2a` or plain `4`:**

- **PDF/A-2a is not available here.** PDF/A-2 is built on PDF 1.7 and its file header must read `%PDF-1.n`. PDF/UA-2 requires PDF 2.0. The two standards are mutually exclusive — you cannot have both. PDF/A-4 is the PDF 2.0-era part, and it is the one that pairs with PDF/UA-2. (If some external system insists on literal PDF/A-2a, you must drop to `pdfstandard={ua-1, a-2a}` with `pdfversion=1.7` and give up PDF/UA-2.)
- **Plain PDF/A-4 fails.** LaTeX's UA-2 tagging attaches two small CSS stylesheets as *associated files* (they carry the HTML mapping for lists and math). PDF/A-4 base requires every embedded file to itself be PDF/A, so those stylesheets trip rule 6.9-3. The **`f`** conformance level is defined precisely to permit arbitrary embedded files, so `a-4f` is the correct declaration — it is not a weaker claim about tagging or color.

Adding `pdfstandard=a-4f` is also what pulls in the sRGB output intent and the PDF/A identification schema automatically; no `colorprofiles` package call is needed.

For more detail, inspect the PDF catalog directly:

```bash
root=$(qpdf --show-object=trailer csuf_template.pdf | grep -oE "/Root [0-9]+" | awk '{print $2}')
qpdf --show-object=$root csuf_template.pdf
```

A properly tagged file lists `/StructTreeRoot`, `/MarkInfo`, and `/Lang`:

```
<< /AF ... /Lang (en-US) /MarkInfo 29 0 R /StructTreeRoot 5 0 R /Type /Catalog ... >>
```

If `/StructTreeRoot` is absent, the file is not tagged. (Don't try to `grep` the PDF itself for that string — it lives inside compressed object streams.)

### What actually turns tagging on

Tagging is activated in the `\DocumentMetadata` block at the very top of each `.tex` file:

```latex
\DocumentMetadata{
  pdfstandard=ua-2,
  pdfstandard=a-4f,
  pdfversion=2.0,
  lang=en-US,
  testphase={phase-III, math, table, firstaid, sec, title}  % <- this activates tagging
}
```

**Do not delete the `testphase` line.** It is the part that does the work:

- `pdfstandard=ua-2` only *declares* conformance. Older LaTeX kernels inferred tagging from it; **current kernels do not.**
- Loading `tagpdf` and calling `\tagpdfsetup{activate-all=true}` does **not** activate tagging on its own either.

Without an explicit activation line you get a clean compile and an untagged PDF. This is a real regression that has silently broken previously-working documents: recompiling an untouched `.tex` on a newer TeX Live can turn a tagged PDF into an untagged one.

On **LaTeX 2025-06-01 or newer** you may use `tagging=on` in place of `testphase={...}`; both work. These templates keep `testphase` because it also works on older distributions, including whatever Overleaf is currently running.

---

## License

**[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](LICENSE)**

You are free to:
* **Share** — copy and redistribute in any medium or format
* **Adapt** — remix, transform, and build upon the material

Under these terms:
* **Attribution** — Give appropriate credit and indicate changes
* **NonCommercial** — No commercial use
* **ShareAlike** — Distribute contributions under the same license

---

## Contact & Workshop Materials

**David P. Adams** – Cal State Fullerton  
📧 [dpadams@fullerton.edu](mailto:dpadams@fullerton.edu)

*For questions, suggestions, or additional workshop materials.*
