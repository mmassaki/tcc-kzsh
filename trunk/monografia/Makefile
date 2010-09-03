all: clean figures compile show

clean:
	/bin/rm -fr *.log *.aux *.bbl *.blg *.dvi *.pdf *.idx *.lot *.lof *.out *.ps *.toc *.bb

figures:
	$(shell cd ./capitulos/figuras; ebb *.png; ebb *.jpg)	

show: monografia.pdf
	MACHINE= $(shell uname -s)
	ifeq ($(shell uname -s),Darwin)
		$(shell open monografia.pdf)
	else
		ifeq ($(MACHINE),Linux)
			$(shell acroread monografia.pdf)
		else
			xpdf monografia.pdf
		endif
	endif

compile: monografia.tex
	latex $< ; latex $< ; bibtex $(<:.tex=) ; latex $< ; latex $< ; dvipdfm -p a4 -o $(<:.tex=.pdf) $(<:.tex=.dvi)
