ALL=$(wildcard *.sty *.tex figs/*.svg)
PAPER=main
SHELL=/bin/zsh

FIGS_SVG=$(wildcard figs/*.svg)
FIGS_PDF=$(FIGS_SVG:%.svg=%.pdf)

./figs/%.pdf: ./figs/%.svg  ## Figures for the manuscript
	inkscape -D -z --file=$< --export-pdf=$@ --export-latex


all: $(FIGS_PDF) ## Build full thesis (LaTeX + figures)
	pdflatex $(PAPER)
	pdflatex $(PAPER)
	bibtex $(PAPER)
	pdflatex $(PAPER)
	pdflatex $(PAPER)

clean:  ## Clean LaTeX and output figure files
	rm -f *.out *.aux *.log *.blg *.bbl
	rm -f $(FIGS_PDF)

#watch:  ## Recompile on any update of LaTeX or SVG sources
#    @while [ 1 ]; do; inotifywait $(ALL); sleep 0.01; make all; done
