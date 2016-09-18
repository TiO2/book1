# book

[![Documentation Status](https://readthedocs.org/projects/book1/badge/?version=latest)](http://book1.readthedocs.io/zh_CN/latest/?badge=latest)

For more information see the [documentation][docs].

[docs]: http://book1.readthedocs.io



Some error handling:

- image too large when compiling the latex (either xelatex or pdflatex on readthedocs.com): 
After running the JPG image through the conversion tool of Image Magick convert, i.e. convert a_lipid_CG.jpg a_lipid_CG2.jpg and testing the document with this new JPG file, the error disappears. This leads me to the conclusion that your particular JPG file is not fully compatible with XeTeX. Apparently XeTeX has issues reading the size from the meta-data from the JPG, which somehow leads to the "too-large" error.

To fix this please open the JPG file in an image manipulation program and save it again. 






