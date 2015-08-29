HTMLOPTS = --katex -c index.css --smart -t html5

all: clean index.html
clean:; rm *.html
%.html: %.md; pandoc $< $(HTMLOPTS) -s -o $@
%.pdf: %.md; pandoc $< -s -o $@