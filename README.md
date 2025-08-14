# CSUF LaTeX Syllabus Templates

This repository contains LaTeX syllabus templates for California State University, Fullerton (CSUF) faculty.  
It includes two files:

- **`csuf_template.tex`** – A complete, ready-to-use syllabus template.
- **`csuf_template_shell.tex`** – A minimal “shell” version for those who want to add their own structure and content.

Both templates are designed to be **university-compliant**, **accessible**, and easy to adapt for different courses.

---

## Features

- CSUF branding and logo
- LuaLaTeX-compatible formatting
- Built-in structure for common syllabus sections (course info, policies, schedule, etc.)
- Consistent, professional typography
- Fully editable in any LaTeX environment

---

## Requirements

To compile the templates, you’ll need:

- **LaTeX distribution** (e.g., TeX Live or MikTeX)
- **LuaLaTeX** compiler
- `csuf_logo.png` in the same directory as `csuf_template.tex`
- Recommended editor: [TeXstudio](https://www.texstudio.org/) or [Overleaf](https://www.overleaf.com/)

---

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/CSUF-MPA/csuf-syllabus.git
   ```


2. Place `csuf_logo.png` in the same directory as the `.tex` files.
3. Compile using:

   ```bash
   lualatex csuf_template.tex
   ```
4. For a stripped-down starting point, use:

   ```bash
   lualatex csuf_template_shell.tex
   ```

---

## Customization

* Replace placeholder text with your own course information.
* Add or remove sections as needed.
* Adjust formatting using standard LaTeX commands.

---

## License

These templates are shared for **educational and professional use** by CSUF faculty and staff.
Please retain attribution when redistributing.

---

## Contact

For questions, suggestions, or workshop materials, contact:
**David P. Adams** – MPA Director, CSUF
📧 [dpadams@fullerton.edu](mailto:dpadams@fullerton.edu)

