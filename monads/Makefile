HTMLOPTS = --katex -c index.css --smart -t html5 --highlight-style=monochrome

all: clean index.html index.pdf
clean:; rm *.html
%.html: %.md; pandoc $< $(HTMLOPTS) -s -o $@
%.pdf: %.md; pandoc $< -s -o $@