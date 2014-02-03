##

TARGET = sampleresume

# used for tex -> pdf generation
TEXFILES = $(wildcard *.tex)
TEXFILE = $(TARGET).tex
BIBFILE = ../bib/Main.bib
PDF = $(TARGET).pdf
HTML = $(TARGET).html


all: clean $(PDF)

hicamp: clean wrapper_hicamp.pdf 
	-killall Preview
	sleep 1
	open wrapper_hicamp.pdf

html: clean $(HTML)

%.pdf: %.tex #$(BIBFILE) # %.blg %.toc $(TEXFILES)
	pdflatex -interaction=nonstopmode $*.tex
	pdflatex -interaction=nonstopmode $*.tex
	#pdflatex -interaction=nonstopmode $*.tex
	#pdflatex -interaction=nonstopmode $*.tex
	\rm -rf *.dvi *.aux *.ps *~ *.log *.out *.lot *.lof *.toc *.blg *.bbl url.sty nain.cb nain.cb2

%.ps: %.tex $(BIBFILE) # %.blg %.toc $(TEXFILES)
	latex -interaction=nonstopmode $*.tex
	bibtex $*
	latex -interaction=nonstopmode $*.tex
	latex -interaction=nonstopmode $*.tex
	dvips -o $(TARGET).ps $(TARGET).dvi

%.html: %.pdf
	latex2html -split 0 -white -html_version 4.0 -show_section_numbers -local_icons -no_navigation $*.tex

clean:
	\rm -rf $(PDF)
	\rm -rf $(TARGET)
	\rm -rf *.pdf
	\rm -rf *.dvi *.aux *.ps *~ *.log *.out *.lot *.lof *.toc *.blg *.bbl url.sty nain.cb nain.cb2

view:   
	pdflatex $(TARGET).tex
	acroread $(PDF)

osx:
	open $(PDF)

open: all
	-killall Preview
	sleep 1
	open $(PDF)
