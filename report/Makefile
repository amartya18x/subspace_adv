DIR=$(PWD)
ALL=$(wildcard *.sty *.tex $(DIR)/figures/*.svg)
PAPER=main
SHELL=/bin/zsh


FIGS_SVG=$(wildcard figs/*.svg)
FIGS_PDF=$(FIGS_SVG:%.svg=%.pdf)


$(DIR)/figures/%.pdf: $(DIR)/figures/%.svg  ## Figures for the manuscript
	inkscape -D  $< --export-filename=$@ --export-latex


all: $(FIGS_PDF)  ## Build full thesis (LaTeX + figures)
	pdflatex $(PAPER)
	pdflatex $(PAPER)
	bibtex $(PAPER)
	pdflatex $(PAPER)
	pdflatex $(PAPER)

#clean:  ## Clean LaTeX and output figure files
#    rm -f *.nav *.snm *.out *.aux *.log *.fls *.blg *.bbl
#    rm -f $(FIGURES_PDF)

#watch:  ## Recompile on any update of LaTeX or SVG sources
#    @while [ 1 ]; do; inotifywait $(ALL); sleep 0.01; make all; done
