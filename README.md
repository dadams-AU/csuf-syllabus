# CSUF LaTeX Syllabus Templates

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

This repository contains LaTeX syllabus templates for California State University, Fullerton (CSUF) faculty.  
The templates are designed to be **university-compliant**, **accessible**, and easy to adapt for different courses.

---

## Repository Structure

```

csuf-syllabus/
├── csuf\_template/        # Complete, ready-to-use syllabus template
├── csuf\_template\_shell/  # Minimal “shell” template for customization
├── csuf_logo.png         # CSUF logo image (required for templates)
├── example/        # Example syllabus showcasing template usage
├── .gitignore
├── LICENSE
└── README.md

````

---

## Features

- CSUF branding and logo
- Accessibility-ready (PDF/UA tagging with `tagpdf` + `DocumentMetadata`)
- LuaLaTeX-compatible formatting
- Built-in structure for common syllabus sections (course info, policies, schedule, etc.)
- Consistent, professional typography (TeX Gyre fonts with fallback to Latin Modern)
- Fully editable in any LaTeX environment

---

## Requirements

To compile the templates, you’ll need:

- **LuaLaTeX** compiler (XeLaTeX/PDFLaTeX will not work with accessibility tagging)
- **LaTeX distribution** (TeX Live 2023+, MiKTeX, or MacTeX)
- `csuf_logo.png` in the template directory
- Editor of choice: [Overleaf](https://www.overleaf.com/) (easiest), [TeXstudio](https://www.texstudio.org/), or another LaTeX editor

### Key packages

The template depends on:

- `tagpdf` (for PDF/UA tagging)
- `pdfmanagement-testphase`
- `fontspec`
- `tex-gyre` font families

These are installed by default on Overleaf. On local machines you may need to install or update them manually (see below).

---

## Installation Notes

### Overleaf (recommended)
1. Upload the repo or clone directly into Overleaf.  
2. Go to **Menu → Compiler → LuaLaTeX**.  
3. Click **Recompile**.  
That’s it—no package installs required.

### Local TeX Live

Update and install required packages:

```bash
tlmgr update --self --all
tlmgr install tagpdf tex-gyre tex-gyre-math fontspec
````

### Linux Packages

* **Ubuntu/Debian**

  ```bash
  sudo apt install texlive-luatex texlive-latex-extra fonts-texgyre
  ```
* **Arch/Manjaro**

  ```bash
  sudo pacman -S texlive-latexextra texlive-fontsextra
  ```

### macOS (MacTeX)

Use **TeX Live Utility** to install `tagpdf` and `tex-gyre`.

### Windows (MiKTeX)

Open **MiKTeX Console** → Settings → enable *Install missing packages on-the-fly*.
If needed, search for `tagpdf` and install manually.

---

## Usage

1. Clone this repository:

   ```bash
   git clone https://github.com/CSUF-MPA/csuf-syllabus.git
   ```
2. Open either `csuf_template/` (full) or `csuf_template_shell/` (minimal).
3. Compile with:

   ```bash
   lualatex csuf_template.tex
   ```

   or

   ```bash
   lualatex csuf_template_shell.tex
   ```

If `tagpdf` or TeX Gyre fonts are not installed, the templates will still compile using fallbacks (but without accessibility tagging).

---

## Quick Troubleshooting

| Error message               | Fix                                                                                   |
| --------------------------- | ------------------------------------------------------------------------------------- |
| `tagpdf-base.sty not found` | Install `tagpdf` (`tlmgr install tagpdf`), or use Overleaf                            |
| `fontspec.sty not found`    | Install LuaLaTeX support (`tlmgr install fontspec`)                                   |
| TeX Gyre fonts missing      | Install fonts (`tlmgr install tex-gyre tex-gyre-math` \| `apt install fonts-texgyre`) |
| Output looks odd / metadata | Double-check compiler = **LuaLaTeX**                                                  |

Verification commands (local only):

```bash
kpsewhich tagpdf-base.sty
kpsewhich texgyretermes-regular.otf
```

If all else fails → use Overleaf.

---

## Customization

* Replace placeholder text with your course information.
* Add/remove sections as needed.
* Adjust formatting using standard LaTeX commands.
* Fallbacks ensure the file compiles even without `tagpdf` or TeX Gyre.

---

## License

This work is licensed under the
**[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](LICENSE)**.

You are free to:

* **Share** — copy and redistribute the material in any medium or format
* **Adapt** — remix, transform, and build upon the material

Under the following terms:

* **Attribution** — Give appropriate credit, link to the license, and indicate if changes were made.
* **NonCommercial** — You may not use the material for commercial purposes.
* **ShareAlike** — If you remix, transform, or build upon the material, you must distribute your contributions under the same license.

---

## Contact

For questions, suggestions, or workshop materials, contact:

**David P. Adams** – Cal State Fullerton

📧 [dpadams@fullerton.edu](mailto:dpadams@fullerton.edu)