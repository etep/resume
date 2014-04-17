##

TARGET = StevensonJohnPResume

# used for tex -> pdf generation
TEXFILES = $(wildcard *.tex)
TEXFILE = $(TARGET).tex
BIBFILE = ../bib/Main.bib
PDF = $(TARGET).pdf
HTML = $(TARGET).html


all: clean $(PDF)

html: clean $(HTML)

%.pdf: %.tex
	mkdir -p ../pdf
	pdflatex -interaction=nonstopmode $*.tex
	\rm -rf *.dvi *.aux *.ps *~ *.log *.out *.lot *.lof *.toc *.blg *.bbl url.sty nain.cb nain.cb2
	mv $(PDF) ../pdf

%.html: %.pdf
	latex2html -split 0 -white -html_version 4.0 -show_section_numbers -local_icons -no_navigation $*.tex

clean:
	\rm -rf ../pdf/$(PDF)
	\rm -rf $(TARGET)
	\rm -rf *.pdf
	\rm -rf *.dvi *.aux *.ps *~ *.log *.out *.lot *.lof *.toc *.blg *.bbl url.sty

# linux?
view:   
	pdflatex $(TARGET).tex
	acroread $(PDF)

# mac
open: all
	-killall Preview
	sleep 1
	open ../pdf/$(PDF)
