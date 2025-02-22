FILES = $(patsubst %.md, %.docx, $(wildcard *.md))
FILES += $(patsubst %.md, %.pdf, $(wildcard *.md))

FILTERS =
OPTIONS =
PDF_ENGINE =
PDF_OPTIONS =
FORMAT_OPTIONS =
CSL_PATH = $(HOME)/.pandoc/csl/gost-r-7-0-5-2008-numeric.csl

### Cross references
## Use pandoc-xnos (https://github.com/tomduck/pandoc-xnos)
## Local pandoc-xnos
# FILTERS += --filter pandoc/filters/pandoc_fignos.py --filter pandoc/filters/pandoc_eqnos.py --filter pandoc/filters/pandoc_tablenos.py --filter pandoc/filters/pandoc_secnos.py
## System-wide pandoc-xnos
# FILTERS += --filter pandoc-fignos --filter pandoc-eqnos --filter pandoc-tablenos --filter pandoc-secnos
## Use pandoc-crossref (https://github.com/lierdakil/pandoc-crossref)
FILTERS += --filter pandoc-crossref
###
PDF_ENGINE += --pdf-engine=xelatex --pdf-engine-opt=--shell-escape
OPTIONS += --number-sections
BIB_OPTIONS = --citeproc

report.docx: report.md
	pandoc "report.md" --filter pandoc-crossref --number-sections --citeproc --csl $(CSL_PATH) -o "report.docx"

report.pdf: report.md
	pandoc "report.md" --filter pandoc-crossref --pdf-engine=xelatex --pdf-engine-opt=--shell-escape  --citeproc --csl $(CSL_PATH) --number-sections -o "report.pdf"
 
all: $(FILES)


clean:
	-rm $(FILES) *~

cleanall: clean
