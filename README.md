# TikZ Scripts
This repo contains a few scripts I wrote for dealing with matlab2tikz generated tikz figure.

## tikzsimplify
This is probably the most useful. If you give it a matlab2tikz generated `.tex`
file, it will perform the [Visvalingam–Whyatt algorithm][1] to simplify the paths
within. This can greatly reduce the rendering time of the TikZ figure, as well
as reduce the size of the resultant PDF file. The minimum resolution will need
to be specified; I recommend around `(axis width)*(axis height)/(res * (target
width in cm)*(target height in cm))` where `res ~= 400-600 pix/cm^2`.

Usage:
```
python fig.tex tol > fig-clean.tex
```

It's written in python3, but should also work in python2.7.

## pdf2pdf
Modified version of eps2eps. In most cases it will reduce the size of a PDF file.

Unix/Cygwin only.  Requires ghostscript.

## tikz2pdf
Generates a cropped and minimized PDF of a TikZ `.tex` figure. You may want to
edit it to import whatever packages you're using.

Unix/Cygwin only. Requires latex, ghostscript and pdfcrop.


[1]: https://hydra.hull.ac.uk/resources/hull:8338
