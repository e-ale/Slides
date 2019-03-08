DOCS = petazzoni-buildroot-tutorial.pdf petazzoni-buildroot-tutorial-lab.pdf \
       woerner-buildroot-tutorial.pdf

PICTURES = \
	$(patsubst %.dia,%.pdf,$(wildcard *.dia */*.dia)) \
        $(patsubst %.svg,%.pdf,$(wildcard *.svg */*.svg)) \
        $(patsubst %.eps,%.pdf,$(wildcard *.eps */*.eps))

all: $(PICTURES) $(DOCS)

%.pdf: %.tex
	$(PDFLATEX_ENV) xelatex -shell-escape $^
	$(PDFLATEX_ENV) xelatex -shell-escape $^

%.pdf: %.svg
	inkscape -D -A $@ $<

%.pdf: %.eps
	epstopdf --outfile=$@ $^

%.eps: %.dia
	dia -e $@ -t eps $^

clean:
	$(RM) -r bootlin/*.pdf toganlabs/*.pdf *.pdf *.pyg *.snm *.toc *.vrb *.aux *.nav *.out *.dia~ *.log _minted* $(PICTURES)
