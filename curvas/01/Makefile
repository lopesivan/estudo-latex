SRCS = $(shell ls *.tex)
EXT  = ps dvi pdf bak log aux nav out snm toc vrb
OUT  = $(foreach s,$(SRCS), $(addprefix $(s:.tex=.), $(EXT)))

#PDFLATEX  = xelatex
PDFLATEX  = pdflatex

READER    = evince
#READER    = acroread

PDF       = $(SRCS:.tex=.pdf)

TARGETS   = $(PDF)

all: $(TARGETS)

##\### ls *.tex| sed 's/.*/echo `basename & .tex`.pdf: &/'| sh | sed 's/.*/&\n\t\$(PDFLATEX) \$^/'>> Makefile
##\
# tex -> pdf
%.pdf:  %.tex
	$(PDFLATEX) $^
	$(PDFLATEX) $^

show:
	for pdf in *.pdf; do \
		zathura $$pdf; \
	done

clean:
	/bin/rm -rf $(TARGETS) *~ $(OUT) "`pwd| sed 's=.*/=='`".tgz

dist:
	tar cvzf "`pwd| sed 's=.*/=='`".tgz *

# END OF FILE
