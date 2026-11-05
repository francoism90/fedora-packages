# COPR "make srpm" entry point: make -f .copr/Makefile srpm outdir=<dir> spec=<path>
spec ?= $(firstword $(wildcard *.spec))
outdir ?= .
srcdir := $(dir $(abspath $(spec)))

.PHONY: srpm
srpm:
	rpmbuild -bs \
		--define "_sourcedir $(srcdir)" \
		--define "_srcrpmdir $(abspath $(outdir))" \
		--define "_disable_source_fetch 0" \
		$(spec)
