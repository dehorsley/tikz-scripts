# TikZ Scripts (unmaintained)
This repo contains a few scripts I wrote for dealing with matlab2tikz generated tikz figure.

## tikzsimplify
**This functionality has now been merged into the `cleanfigure` function of [matlab2tikz](http://github.com/matlab2tikz/matlab2tikz). You probably want to use that.**
```
tikzsimplify [-h] [-t tol] [-v] [-i] [-o outfile.tex] infile.tex
optional arguments:
  -h, --help      show this help message and exit
  -t tol          tolerence of simplify algorithm (defaults to best guess)
  -v, --verbose   print info to stderr
  -i, --in-place  overwrite input file after simplification
  -o outfile.tex  output to outfile.tex rather than stdout
```
This is probably the most useful script here. If you give it a matlab2tikz
generated `.tex` file, it will perform the [Visvalingam–Whyatt algorithm][1] to
simplify the paths within. This should stop TeX running out of memory, greatly
reduce the rendering time of the TikZ figure and reduce the size of the
resultant PDF file.

The script will attempt to guess a good tolerance for the simplification
algorithm by assuming your figure is around 15cm by 9 cm. If you intend to print
the figure larger than this, you will need to specify a tolerance in the `tol`
parameter.  I recommend around `(axis width)*(axis height)/(res * (target width in
cm)*(target height in cm))` where `res~=400-600 pix/cm^2`.

By default, `matlab2tikz` limits the number of points in a plot in an attempt
to stop TeX running out of memory. If a plot has more than the `maxChunkLength`
parameter, which is 4000 by default, `matlab2tikz` splits into sub plots. This
can cause artifacts for dashed lines but also prevents this simplify script from
running optimally.

To prevent this, I recommend you export your figure with `matlab2tikz(...,'maxChunkLength',Inf)`

I highly recommend running this in [PyPy 2.5][PyPy] instead of the
usual python interpreter as it gives about a 25x speed improvement.

## pdf2pdf
Modified version of eps2eps. In most cases it will reduce the size of a PDF file.

Unix/Cygwin only.  Requires ghostscript.

## tikz2pdf
Generates a cropped and minimized PDF of a TikZ `.tex` figure. You may want to
edit this script to import whatever packages you're using.

Unix/Cygwin only. Requires latex, ghostscript and pdfcrop.


[PyPy]: http://pypy.org/
[1]: https://hydra.hull.ac.uk/resources/hull:8338
