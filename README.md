# ISR-401 · Evaluación de la Unidad I (EV-PRAC-01)

Transcripción fiel de la prueba práctica del caso FRÍOVAC (Ingeniería de Requerimientos, UTEQ).

## Estructura de `EV-PRAC-01/`

```
EV-PRAC-01/
├── main.tex          # archivo principal
├── main.pdf          # PDF compilado
├── referencias.bib   # bibliografía (BibTeX)
├── figuras/
│   └── logoband.png  # logo institucional
└── evidencias/
    ├── hoja-01.jpeg
    ├── hoja-02.jpeg
    └── hoja-03.jpeg  # fotografías de las hojas (anexo)
```

## Datos de compilación

| Ítem | Valor |
|---|---|
| Archivo principal | `main.tex` |
| Compilador | `pdfLaTeX` (no usar XeLaTeX ni LuaLaTeX) |
| Bibliografía | `BibTeX` (no Biber) |
| Orden de comandos | `pdflatex` → `bibtex` → `pdflatex` → `pdflatex` |
| Carpeta desde donde compilar | `EV-PRAC-01/` (las rutas `figuras/` y `evidencias/` son relativas a `main.tex`) |

### Dependencias (paquetes LaTeX)

`inputenc`, `fontenc`, `helvet`, `geometry`, `graphicx`, `array`, `tabularx`, `longtable`,
`pdflscape`, `colortbl`, `xcolor`, `enumitem`, `fancyhdr`, `lastpage`, `tcolorbox` (con la
biblioteca `most`), `amsmath`, `natbib`, `url`, `needspace`, `caption`, `hyperref`.

## Opción A: compilar en Windows con MiKTeX

1. Instale [MiKTeX](https://miktex.org/download). En el asistente, en
   «Install missing packages on-the-fly» elija **Yes** (así descarga solo los paquetes que falten).
2. Clone el repositorio y entre a la carpeta de la prueba:
   ```bash
   git clone <URL-del-repositorio>
   cd <repositorio>/EV-PRAC-01
   ```
3. Compile en este orden:
   ```bash
   pdflatex main.tex
   bibtex main
   pdflatex main.tex
   pdflatex main.tex
   ```
4. El resultado es `main.pdf`, en la misma carpeta.

Si usa TeXworks o TeXstudio con MiKTeX: abra `main.tex`, elija el compilador **pdfLaTeX**, y
ejecute *PDFLaTeX → BibTeX → PDFLaTeX → PDFLaTeX* (en TeXstudio basta con «Compilar y
ver» tras configurar la herramienta de bibliografía en BibTeX).

## Opción B: compilar en Linux (TeX Live)

```bash
sudo apt install texlive-latex-base texlive-latex-extra texlive-fonts-recommended \
                 texlive-science texlive-bibtex-extra
cd EV-PRAC-01
pdflatex main.tex && bibtex main && pdflatex main.tex && pdflatex main.tex
```

## Opción C: compilar en Overleaf

1. Comprima la carpeta `EV-PRAC-01/` en un `.zip` que contenga `main.tex`, `referencias.bib`,
   `figuras/` y `evidencias/`.
2. En Overleaf: **New Project → Upload Project** y suba el `.zip`.
   (Alternativa: **New Project → Import from GitHub**, si tiene la cuenta enlazada.)
3. Abra **Menu** (arriba a la izquierda) y verifique:
   - **Main document:** `main.tex`
   - **Compiler:** `pdfLaTeX`
   - **TeX Live version:** 2023 o superior
4. Pulse **Recompile**. Overleaf ejecuta BibTeX y las pasadas necesarias de forma automática.
5. Descargue el PDF con **Download PDF**.

> Si subió el `.zip` con la carpeta `EV-PRAC-01/` adentro, Overleaf la mostrará como una
> subcarpeta. En ese caso, marque `EV-PRAC-01/main.tex` como *Main document*.

## Posibles fallos y cómo resolverlos

| Mensaje o síntoma | Causa | Solución |
|---|---|---|
| `File 'figuras/logoband.png' not found` | Falta el logo o se compila desde otra carpeta | Verifique que exista `figuras/logoband.png` y compile desde dentro de `EV-PRAC-01/` |
| En el PDF aparece `[falta evidencias/hoja-01.jpeg]` | Las fotos no están o tienen otro nombre/extensión | Ponga las fotos en `evidencias/` con los nombres exactos `hoja-01.jpeg`, `hoja-02.jpeg`, `hoja-03.jpeg` (en minúsculas, y `.jpeg`, no `.jpg`) |
| `Citation ... undefined`, `No file main.bbl`, citas como `[?]` | No se ejecutó BibTeX | Siga el orden completo: `pdflatex` → `bibtex` → `pdflatex` → `pdflatex` |
| `Reference 'LastPage' undefined` o `Reference 'tab:alineacion' undefined` | Faltan pasadas de `pdflatex` | Compile una o dos veces más |
| `LaTeX Error: File 'xxx.sty' not found` | Falta un paquete (típico en MiKTeX o TeX Live mínimo) | MiKTeX: acepte la instalación automática o use *MiKTeX Console → Packages*. TeX Live: instale `texlive-latex-extra` y `texlive-science` |
| MiKTeX muestra una ventana «Install missing packages» y se queda esperando | Pide confirmación para instalar | Pulse *Install*; si falla, ejecute *MiKTeX Console → Check for updates* y reintente |
| `Underfull \hbox` / `Overfull \hbox` | Aviso de espaciado de línea | Es solo una advertencia; no afecta el PDF |
| El editor usa XeLaTeX/LuaLaTeX o Biber y falla | Compilador equivocado | Cambie a `pdfLaTeX` y `BibTeX` |
| Caracteres raros (`Ã³`, `Ã±`) en el texto | El `.tex` no está guardado en UTF-8 | Guarde `main.tex` con codificación UTF-8 |
| Overleaf: `File not found` con la subcarpeta | El zip incluye una carpeta extra y el *Main document* apunta mal | En *Menu* elija el `main.tex` correcto |
| Overleaf: «Compile timeout» | Imágenes muy pesadas | Reduzca las fotos a ≤ 2 MB cada una |
| Imagen de la foto muy grande o rotada | Orientación EXIF del teléfono | Rote y guarde la imagen con un editor antes de subirla |
| El PDF no se actualiza | Archivos auxiliares viejos | Borre `main.aux`, `main.bbl`, `main.out`, `main.log` y compile de nuevo |

## Entrega

1. Primer commit: solo `evidencias/` (fotografías).
2. Siguientes commits: `main.tex`, `referencias.bib`, `figuras/`, `main.pdf` y este `README.md`.
3. `git push` y verifique en GitHub que el repositorio es público y que abre la URL.

