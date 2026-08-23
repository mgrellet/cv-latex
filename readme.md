# cv-latex

CVs and cover letters in LaTeX. Compile to PDF with `pdflatex`.

## Online editors

- https://app.crixet.com/
- https://prism.openai.com/
- https://8gwifi.org/latex/editor.jsp

## Local requirements

What is installed on this machine (macOS) to **read, generate, and process** `.tex` and `.pdf` files. Windows equivalents are listed below.

### macOS (this machine)

| What | What for | How it was installed |
| --- | --- | --- |
| [Homebrew](https://brew.sh/) | Package manager | Homebrew installer |
| **BasicTeX** (TeX Live 2026) | Compile `.tex` → `.pdf` (`pdflatex`, `xelatex`, `lualatex`, `tlmgr`) | `brew install --cask basictex` |
| Extra packages: `enumitem`, `needspace` | Used by the CVs in this repo; not included in BasicTeX | `tlmgr --usermode install enumitem needspace` |
| **Preview** (built into macOS) | Open / read PDFs | Comes with the OS |
| Text editor (Cursor, CotEditor, etc.) | Edit `.tex` | Apps in `/Applications` |

Install from scratch:

```bash
# 1. Homebrew (if missing)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Lightweight LaTeX distro (~100 MB). Full alternative: MacTeX (`brew install --cask mactex`)
brew install --cask basictex

# 3. Reload PATH (or open a new terminal) so pdflatex is available
eval "$(/usr/libexec/path_helper)"
export PATH="/Library/TeX/texbin:$PATH"

# 4. Packages used by these CVs that BasicTeX does not ship
tlmgr --usermode init-usertree
tlmgr --usermode install enumitem needspace
```

`--usermode` installs into `~/Library/texmf/` (no sudo). They were added when compiling the PedidosYa CVs because BasicTeX is a minimal distro and those two packages were missing.

Verify:

```bash
which pdflatex          # /Library/TeX/texbin/pdflatex
pdflatex --version      # pdfTeX ... (TeX Live 2026)
```

Open a PDF:

```bash
open file.pdf           # Preview
```

### Windows

| What | What for | How to install |
| --- | --- | --- |
| **MiKTeX** (recommended) | Compile `.tex` → `.pdf`. Installs missing packages on demand (`enumitem`, `needspace`, etc.) | [miktex.org](https://miktex.org/download) or `winget install MiKTeX.MiKTeX` |
| **TeX Live** (alternative) | Same role, larger install (MacTeX equivalent) | [tug.org/texlive](https://tug.org/texlive/) or `winget install TeXLive.TeXLive` |
| PDF viewer | Read PDFs | Edge / Chrome, or [SumatraPDF](https://www.sumatrapdfreader.org/) (`winget install SumatraPDF.SumatraPDF`) |
| Text editor | Edit `.tex` | VS Code / Cursor, Notepad++, TeXstudio |

With **winget** (Windows 10/11):

```powershell
winget install MiKTeX.MiKTeX
winget install SumatraPDF.SumatraPDF
```

With **Chocolatey**:

```powershell
choco install miktex
choco install sumatrapdf
```

After installing MiKTeX, close and reopen the terminal, then verify:

```powershell
pdflatex --version
```

MiKTeX usually prompts to install missing packages the first time you compile; accept the automatic install.

## Compile a CV

From the folder that contains the `.tex` file (run it **twice** if there are links / `hyperref`):

```bash
pdflatex -interaction=nonstopmode cv-peya-spanish.tex
```

Example:

```bash
cd peya
pdflatex -interaction=nonstopmode cv-peya-spanish.tex
pdflatex -interaction=nonstopmode cover-letter-peya.tex
```

The `.pdf` is written next to the `.tex`. `.aux`, `.log`, and `.out` are build artifacts; you can ignore or delete them.
