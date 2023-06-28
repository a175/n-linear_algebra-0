PDFLATEX=dvipdfmx
LATEX=platex
#BIBTEX=bibtex
BIBTEX=pbibtex
DVI2PDF=dvipdfmx
TEXFILE=x2
MAINTEXFILES=p.tex a.tex numberedproof.sty b.tex
MENDEX=mendex
DICFILE=terms.dic

all: pdf
dvi: ${TEXFILE}.dvi
pdf: ${TEXFILE}.pdf

${TEXFILE}.dvi: ${TEXFILE}.tex ${MAINTEXFILES} ${TEXFILE}.bbl ${TEXFILE}.ind
	${LATEX} ${TEXFILE} && ${LATEX} ${TEXFILE}

${TEXFILE}.pdf: ${TEXFILE}.dvi
	${DVI2PDF} ${TEXFILE}.dvi
#${TEXFILE}.pdf: ${TEXFILE}.tex ${MAINTEXFILES} ${TEXFILE}.bbl
#	${PDFLATEX} ${TEXFILE} && ${PDFLATEX} ${TEXFILE}

bbl:${TEXFILE}.bbl
${TEXFILE}.bbl:
	${LATEX} ${TEXFILE} && ${BIBTEX} ${TEXFILE}

ind: ${TEXFILE}.ind
${TEXFILE}.ind:
	${LATEX} ${TEXFILE} && ${MENDEX} -U -d ${DICFILE} ${TEXFILE}

view:
	evince ${TEXFILE}.pdf &
clean:
	rm -f ${TEXFILE}.dvi ${TEXFILE}.pdf ${TEXFILE}.log ${TEXFILE}.aux ${TEXFILE}.bbl ${TEXFILE}.blg texput.log
