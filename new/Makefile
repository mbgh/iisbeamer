SRC    = beamerthemeiis
TEXVER = 2011
VIEWER = okular

## Determine the host the Makefile is running on.
HOST = $(shell hostname)

## Determine the path to the pdflatex binary depending on the current host.
ifeq ($(HOST),muem_mobile)
  ## Path to the latex/pdflatex binary for my cygwin installation on my laptop.
  LATEX_BIN     = "/cygdrive/c/Program Files/MiKTeX 2.9/miktex/bin/x64/latex.exe"
	PDFLATEX_BIN  = "/cygdrive/c/Program Files/MiKTeX 2.9/miktex/bin/x64/pdflatex.exe"
  MAKEINDEX_BIN = "/cygdrive/c/Program Files/MiKTeX 2.9/miktex/bin/x64/makeindex.exe"
else
  ## Otherwise we assume that we are running this Makefile on my work PC.
  LATEX_BIN     = latex-$(TEXVER)
  PDFLATEX_BIN  = pdflatex-$(TEXVER)
  MAKEINDEX_BIN = makeindex-$(TEXVER)
endif

## Determine the host the Makefile is running on.
HOST = $(shell hostname)

all: sty doc

$(SRC).sty: $(SRC).dtx $(SRC).dtx
	@$(LATEX_BIN) $(SRC).ins

$(SRC).pdf: $(SRC).dtx
	@$(PDFLATEX_BIN) $(SRC).dtx

sty: $(SRC).sty

doc: $(SRC).pdf

history: $(SRC).dtx
	@$(MAKEINDEX_BIN) -s gglo.ist -o $(SRC).gls $(SRC).glo

index: $(SRC.dtx)
	@$(MAKEINDEX_BIN) -s gind.ist -o $(SRC).ind $(SRC).idx

view:
	$(VIEWER) $(SRC).pdf &

clean:
	@rm -f *.log *~ *.aux *.glo *.gls *.idx *.ilg *.ind
	@rm -f *.out *.tdo *.toc *.sty *.pdf
