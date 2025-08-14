# CSUF LaTeX Syllabus Templates

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

This repository contains LaTeX syllabus templates for California State University, Fullerton (CSUF) faculty.  
The templates are designed to be **university-compliant**, **accessible**, and easy to adapt for different courses.

---

## Repository Structure

```

csuf-syllabus/
├── csuf\_template/         # Complete, ready-to-use syllabus template
├── csuf\_template\_shell/   # Minimal “shell” template for customization
├── .gitignore
├── LICENSE
└── README.md

```

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

- **LaTeX distribution** (e.g., TeX Live or MiKTeX)
- **LuaLaTeX** compiler
- `csuf_logo.png` in the template directory
- Recommended editor: [TeXstudio](https://www.texstudio.org/) or [Overleaf](https://www.overleaf.com/)

---

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/CSUF-MPA/csuf-syllabus.git
    ```

2. Open either `csuf_template/` or `csuf_template_shell/` in your LaTeX editor.
3. Place `csuf_logo.png` in the same directory as the `.tex` file you are compiling.
4. Compile using:

   ```bash
   lualatex csuf_template.tex
   ```
5. For a stripped-down starting point, use the shell version:

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
**David P. Adams** – MPA Director, CSUF
📧 [dpdams@fullerton.edu](mailto:dpadams@fullerton.edu)

