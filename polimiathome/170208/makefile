
TGTS= \
	pdf/polimi@home-intro.beamer.ref.pdf

TEXS=$(patsubst pdf/%.ref.pdf,%.tex, $(TGTS))


all: all-pdfs

all-pdfs: $(TGTS)

all-tex: $(TEXS)

%.ref.pdf: %.tex
	jslatex $< lualatex
	mv $*.pdf $*.ref.pdf

%.pdf: %.tex
	jslatex $< lualatex --nobibtex

pdf/%.pdf: %.pdf
	mv $< $@

%.tex: %.org  
	emacsclient --eval "(progn (find-file \"$<\") (org-latex-export-to-latex))"

%.beamer.tex: %.org ./org-headers/header_universal.org ./org-headers/header_beamer.org
	emacsclient --eval "(progn (find-file \"$<\") (org-beamer-export-to-latex))"
	mv $*.tex $@

clean:
	rm -rf pdf/*
	rm -rf *.pdf *.pyg *.tex _minted-* *.vrb *.aux *.log *.nav *.out *.pdf *.pyg *.snm *.tex~ *.toc auto temp
