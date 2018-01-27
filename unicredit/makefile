
CURTGT?=180116_dsls_frp.pdf
CURORG=$(patsubst %.pdf, %.org, $(CURTGT))

target: $(CURTGT)

edit:
	emacsclient $(CURORG)

watch-edit: $(CURTGT)
	open $(CURTGT)
	watchman $(CURORG) "make $(CURTGT)"

%.pdf: %.org
	org2pdf $*.org -e xelatex -a ./org-headers/header_beamer_xelatex.org --output $@ -r

clean:
	rm -rf pdf/*
	rm -rf *.pdf *.pyg *.tex _minted-* *.vrb *.aux *.log *.nav *.out *.pdf *.pyg *.snm *.tex~ *.toc auto temp
	rm -f tmp-*
