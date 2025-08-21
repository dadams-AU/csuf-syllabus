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
- Modify accessibility tagging if needed (advanced users only)
- Fallbacks ensure compilation even without optimal setup

---

## Why Accessibility Matters (CSUF Compliance)

The PDF/UA tagging in these templates ensures:
- Screen reader compatibility
- University ADA compliance
- Better searchability
- Future-proofing for accessibility standards

**This isn't optional** - it's required for CSUF syllabi.

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
