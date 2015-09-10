SRC = beamerthemeiis

TEXVER = 2011

VIEWBIN = okular

all: sty doc

$(SRC).sty: $(SRC).dtx $(SRC).dtx
	@latex-$(TEXVER) $(SRC).ins

$(SRC).pdf: $(SRC).dtx
	@pdflatex-$(TEXVER) $(SRC).dtx

sty: $(SRC).sty

doc: $(SRC).pdf

history: $(SRC).dtx
	@makeindex-$(TEXVER) -s gglo.ist -o $(SRC).gls $(SRC).glo

index: $(SRC.dtx)
	@makeindex-$(TEXVER) -s gind.ist -o $(SRC).ind $(SRC).idx

view:
	$(VIEWBIN) $(SRC).pdf &

clean:
	@rm -f *.log *~ *.aux *.glo *.gls *.idx *.ilg *.ind
	@rm -f *.out *.tdo *.toc *.sty *.pdf
