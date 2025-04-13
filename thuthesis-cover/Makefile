#!/usr/bin/env make

TEX := $(wildcard *.tex)
PDF := $(TEX:.tex=.pdf)
COVER_PDF := $(TEX:.tex=-cover.pdf)
CROP_PDF := $(patsubst %.tex,cover-%-crop.pdf,$(TEX))

all: $(CROP_PDF)

cover-%-crop.pdf: %-cover.pdf
	pdfcrop $< $@

%-cover.pdf: %.pdf
	qpdf $< --pages . 1 -- $@

%.pdf: %.tex
	latexmk -xelatex $<

clean:
	latexmk -c
	rm -f $(PDF) $(CROP_PDF) $(COVER_PDF)

.PHONY: all clean
.INTERMEDIATE: $(PDF) $(COVER_PDF)
