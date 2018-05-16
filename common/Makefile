SRC  := $(wildcard index.adoc)
HTML := $(patsubst %.adoc,%.html,$(SRC))
PDF  := $(patsubst %.adoc,%.pdf,$(SRC))

SHELL := /bin/bash

all: $(HTML) $(PDF)

clean:
	rm -f $(HTML) $(PDF) Gemfile Gemfile.lock

Gemfile Gemfile.lock:
	ln -s ../common/$@ .

bundle: Gemfile Gemfile.lock
	bundle

%.html: %.adoc bundle
	bundle exec asciidoctor-revealjs $< --trace

%.pdf: %.html
	decktape reveal $^ $@

open:
	open $(HTML) $(PDF)

.PHONY: bundle all open