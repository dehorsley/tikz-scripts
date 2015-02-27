# TikZ Scripts
This repo contains a few scripts I wrote for dealing with matlab2tikz generated tikz figure.

## tikzsimplify (python 3)
This is probably the most useful. If you give it a matlab2tikz generated `.tex`
file, it will perform the [Visvalingam–Whyatt algorithm](https://hydra.hull.ac.uk/resources/hull:8338) to simplify the paths within. This can greatly reduce the
rendering time of the TikZ figure, as well as reduce the size of the resultant
PDF file. The minimum resolution should be specified.
*TODO:* better documentation

## pdf2pdf
Modified version of eps2eps. In most cases it will reduce the size of a PDF file.

## tikz2pdf
Generates a cropped and minimized PDF based on a TikZ `.tex`
