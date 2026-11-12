# TA-IND-01 - ISO/IEC/IEEE 29148 y tipos de requisitos (Twitch)

Asignatura: Ingeniería de Requerimientos (ISR-401) - SPA 2026-2027

## Estructura

    TA-IND-01/
      main.tex          archivo principal
      referencias.bib   referencias (estilo IEEE, IEEEtran)
      figuras/          capturas propias (captura01_inicio.png, captura02_directo.png, captura03_clips.png)
      main.pdf          PDF compilado

## Compilación

- Distribución: MiKTeX (Windows). Editor: TeXStudio.
- Compilador: pdfLaTeX. Bibliografía: BibTeX.
- Archivo principal: `main.tex`.
- Orden de comandos:

      pdflatex main.tex
      bibtex main
      pdflatex main.tex
      pdflatex main.tex

- En TeXStudio: abrir `main.tex` y pulsar F5 (Compilar y ver) o usar "Herramientas > Automático".
- Paquetes (MiKTeX los instala solos al primer uso): babel, lmodern, geometry, graphicx, booktabs, longtable, array, xcolor, caption, enumitem, setspace, fancyhdr, hyperref, url, IEEEtran.

## Capturas

Guardar en `figuras/` con los nombres indicados. Si falta un archivo, el PDF muestra un recuadro rojo.
