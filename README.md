## A fantastic and awesome book

[![Documentation Status](https://readthedocs.org/projects/book1/badge/?version=latest)](http://book1.readthedocs.io/zh_CN/latest/?badge=latest)

A book written using rst and support Chinese charactors. 

See the html version of the book live: [documentation][docs].

[docs]: http://book1.readthedocs.io

### Tech
Used Sphnix. 

To compile the book locally:  
	cd docs
	# make html
	make html
	# make pdf
	make xelatexpdf


###Some error handling:

- image too large when compiling the latex (either xelatex or pdflatex on readthedocs.com): 
After running the JPG image through the conversion tool of Image Magick convert, i.e. convert a_lipid_CG.jpg a_lipid_CG2.jpg and testing the document with this new JPG file, the error disappears. This leads me to the conclusion that your particular JPG file is not fully compatible with XeTeX. Apparently XeTeX has issues reading the size from the meta-data from the JPG, which somehow leads to the "too-large" error.

To fix this please open the JPG file in an image manipulation program and save it again. 


###XELATEX needed for compling Chinese. 
Updates:
Used the [The ctex Bundle Classes](https://www.overleaf.com/learn/latex/chinese). 


Previously:

https://blog.seisman.info/trash/sphinx-chinese-support/

Add to config.py

import os 
on_rtd = os.environ.get('READTHEDOCS', None) == 'True'
if on_rtd:
    latex_elements = {
    # The paper size ('letterpaper' or 'a4paper').
    #'papersize': 'letterpaper',
    # The font size ('10pt', '11pt' or '12pt').
    #'pointsize': '10pt',
    # Additional stuff for the LaTeX preamble.
    
    'preamble': r'''
    \hypersetup{unicode=true}
    \usepackage{CJKutf8}
    \DeclareUnicodeCharacter{00A0}{\nobreakspace}
    \DeclareUnicodeCharacter{2203}{\ensuremath{\exists}}
    \DeclareUnicodeCharacter{2200}{\ensuremath{\forall}}
    \DeclareUnicodeCharacter{2286}{\ensuremath{\subseteq}}
    \DeclareUnicodeCharacter{2713}{x}
    \DeclareUnicodeCharacter{27FA}{\ensuremath{\Longleftrightarrow}}
    \DeclareUnicodeCharacter{221A}{\ensuremath{\sqrt{}}}
    \DeclareUnicodeCharacter{221B}{\ensuremath{\sqrt[3]{}}}
    \DeclareUnicodeCharacter{2295}{\ensuremath{\oplus}}
    \DeclareUnicodeCharacter{2297}{\ensuremath{\otimes}}
    \begin{CJK}{UTF8}{gbsn}
    \AtEndDocument{\end{CJK}}
    ''',
    }
else:       
    latex_elements = {
         # The paper size ('letterpaper' or 'a4paper').
         #
         # 'papersize': 'letterpaper',

         # The font size ('10pt', '11pt' or '12pt').
         #
         # 'pointsize': '10pt',

         # Additional stuff for the LaTeX preamble.
         #
         # 'preamble': '',

         # Latex figure (float) alignment
         #
         # 'figure_align': 'htbp',        

    'label': '\\usepackage[english]{babel}',
    'papersize': 'letterpaper',
    'pointsize': '12pt',
    #'figure_align': 'H',

    # Additional stuff for the LaTeX preamble.
    'preamble': '''
    \usepackage{xeCJK}
    \usepackage{indentfirst}
    \setlength{\parindent}{2em}
    \setCJKmainfont[BoldFont=SimHei, ItalicFont=FangSong]{SimSun}
    \setCJKmonofont[Scale=0.9]{FangSong}
    \setCJKfamilyfont{song}[BoldFont=SimSun]{SimSun}
    \setCJKfamilyfont{sf}[BoldFont=SimSun]{SimSun}
    \XeTeXlinebreaklocale "zh"
    \XeTeXlinebreakskip = 0pt plus 1pt
    '''     
         
    }
    
    