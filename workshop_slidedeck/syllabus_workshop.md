# CSUF Syllabus Workshop

## GitHub Repository

### Link

https://github.com/dadams-AU/csuf-syllabus

---

## 🚀 Quick Start

### Option 1: Overleaf (Recommended for Beginners)

1. Go to [Overleaf](https://www.overleaf.com/) → login/create account  
2. Upload repo OR clone from GitHub  
3. Menu → Compiler → **LuaLaTeX** (not PDFLaTeX!)  
4. Open `csuf_template/csuf_template.tex`  
5. Click **Recompile** (3–15 sec)  
6. Start customizing!  

---

### Option 2: Local Installation (For Advanced Users)

```bash
git clone https://github.com/CSUF-MPA/csuf-syllabus.git
cd csuf_template
lualatex csuf_template.tex
````

---

## 📂 Repository Structure

```
csuf-syllabus/
├── csuf_template/        # 📄 Ready-to-use template (START HERE)
├── csuf_template_shell/  # 📋 Minimal shell for custom builds
├── csuf_logo.png         # 🏫 CSUF logo (required)
├── example/              # 📚 Example syllabus
├── LICENSE
└── README.md
```

---

## ✨ Key Features

* **CSUF branding + logo** → professional, compliant
* **Accessibility-ready** → PDF/UA tagging (required by CSUF)
* **Modern LuaLaTeX** → better font + unicode handling
* **Built-in structure** → standard syllabus sections included
* **Professional typography** → TeX Gyre fonts w/ fallbacks
* **Cross-platform** → Overleaf, Mac, Windows, Linux

---

## 🚑 Quick Fixes (Local Compiling)

### Always

* Compiler: **LuaLaTeX** (not PDFLaTeX/XeLaTeX)
* Overleaf: Menu → Compiler = LuaLaTeX → Recompile
* Local installs: make sure TeX Live/MiKTeX is up to date

---

### Common Errors & Fixes

**`tagpdf-base.sty not found`**

* Overleaf: already installed
* TeX Live: `tlmgr install tagpdf`
* Ubuntu/Debian: `sudo apt install texlive-fonts-recommended`
* Arch: `sudo pacman -S texlive-fonts-recommended`
* MiKTeX: enable *auto-install missing packages*
* MacTeX: Use TeX Live Utility to install tagpdf and tex-gyre

---

**`fontspec.sty not found`**

* Install LuaLaTeX support

  * TeX Live: `tlmgr install fontspec`
  * Ubuntu/Debian: `sudo apt install texlive-luatex`
  * Arch: `sudo pacman -S texlive-luatex`
  * MacTeX: Use TeX Live Utility to install fontspec

---

**TeX Gyre fonts missing (fallback to Latin Modern)**

* TeX Live:

  ```bash
  tlmgr install tex-gyre tex-gyre-math
  ```
* Ubuntu/Debian: `sudo apt install fonts-texgyre`
* Arch: `sudo pacman -S tex-gyre`
* MacTeX: Use TeX Live Utility to install tex-gyre

---

**Other weird errors**

* Update TeX Live/MiKTeX
* Double-check compiler = **LuaLaTeX**
* If stuck → just use Overleaf

---

## 🔍 Quick Commands (local only)

```bash
# check if tagpdf is installed
kpsewhich tagpdf-base.sty

# check if TeX Gyre is installed
kpsewhich texgyretermes-regular.otf
```

---

## 🔧 Technical Requirements

* **LuaLaTeX** compiler only
* Packages: `tagpdf`, `pdfmanagement-testphase`, `fontspec`, `tex-gyre`
* Keep `csuf_logo.png` in template directory

**Install packages quickly**:

```bash
tlmgr update --self --all
tlmgr install tagpdf tex-gyre tex-gyre-math fontspec
```

---

## 📊 Troubleshooting Flowchart

```
Compile fails?
├── LuaLaTeX?
│   ├── No → Switch to LuaLaTeX
│   └── Yes → Continue
├── On Overleaf?
│   ├── Yes → Should work (contact support)
│   └── No → Local troubleshoot
├── Missing tagpdf?
│   ├── tlmgr install tagpdf
│   └── Still fails → Use Overleaf
├── Font errors?
│   ├── tlmgr install tex-gyre tex-gyre-math
│   └── Still fails → Fallbacks work
└── All else fails → Use Overleaf
```

---

## 📝 Customization

* Replace `[COURSE CODE]`, `[COURSE TITLE]`, etc.
* Update instructor info, schedule, policies
* Add/remove sections as needed
* Fallbacks → still compiles if some fonts/packages missing

---

## ♿ Why Accessibility Matters

* Screen reader compatibility
* ADA/CSUF compliance requirement
* Searchability & future-proofing

👉 **Not optional**: CSUF requires syllabi be accessible.

---

## 📜 License

Creative Commons BY-NC-SA 4.0

* **Share** — copy & redistribute
* **Adapt** — remix & build upon
* **NonCommercial** — no selling
* **ShareAlike** — same license applies

---

## 📬 Contact

**David P. Adams** – Cal State Fullerton
📧 [dpadams@fullerton.edu](mailto:dpadams@fullerton.edu)

For questions or workshop support.
