
CURTGT?=hw_haskell.pdf
CURORG=$(patsubst %.pdf, %.org, $(CURTGT))

ORG2PDFOPTS=--latex-engine lualatex
ORG2PDFOPTSSLIDES=$(ORG2PDFOPTS) --use-header-files ./org-headers/header_beamer.org --exclude-tags notes

target: $(CURTGT)

edit:
	emacsclient $(CURORG)

watch-edit: $(CURTGT)
	open $(CURTGT)
	watchman $(CURORG) "make $(CURTGT)"

%.pdf: %.org
	org2pdf $*.org $(ORG2PDFOPTSSLIDES) --output $@

clean:
	rm -rf pdf/*
	rm -rf *.pdf *.pyg *.tex _minted-* *.vrb *.aux *.log *.nav *.out *.pdf *.pyg *.snm *.tex~ *.toc auto temp
	rm -f tmp-*
