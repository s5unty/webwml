# If this makefile is not generic enough to support a translation,
# please contact debian-www.

WMLBASE=..
CUR_DIR=Bugs
SUBS=

GETTEXTFILES += bugs.mo

CAPATH=$(shell dir=/etc/ssl/ca-debian ; test -d $$dir && echo --ca-directory=$$dir)

include $(WMLBASE)/Make.lang

ifeq "$(LANGUAGE)" "en"
clean::
	rm -f pseudo-packages.description 
endif

$(ENGLISHDIR)/Bugs/pkgreport-opts.inc: \
  $(TEMPLDIR)/common_tags.wml $(GETTEXTDEP) $(call locale,bugs)
	touch $@ # because of $(?F)
index.$(LANGUAGE).html: $(TEMPLDIR)/template.wml $(ENGLISHDIR)/Bugs/footer.inc \
  $(ENGLISHDIR)/Bugs/pkgreport-opts.inc
Access.$(LANGUAGE).html: $(TEMPLDIR)/template.wml otherpages.inc $(ENGLISHDIR)/Bugs/footer.inc
Developer.$(LANGUAGE).html: $(TEMPLDIR)/template.wml otherpages.inc $(ENGLISHDIR)/Bugs/footer.inc
Reporting.$(LANGUAGE).html: $(TEMPLDIR)/template.wml otherpages.inc $(ENGLISHDIR)/Bugs/footer.inc
server-control.$(LANGUAGE).html: $(TEMPLDIR)/template.wml otherpages.inc $(ENGLISHDIR)/Bugs/footer.inc
server-refcard.$(LANGUAGE).html: $(TEMPLDIR)/template.wml otherpages.inc $(ENGLISHDIR)/Bugs/footer.inc
server-request.$(LANGUAGE).html: $(TEMPLDIR)/template.wml otherpages.inc $(ENGLISHDIR)/Bugs/footer.inc
pseudo-packages.$(LANGUAGE).html: $(ENGLISHDIR)/Bugs/pseudo-packages.description \
  $(TEMPLDIR)/template.wml otherpages.inc $(ENGLISHDIR)/Bugs/footer.inc \
  $(ENGLISHDIR)/Bugs/pseudo-packages.inc $(GETTEXTDEP)

.PHONY: $(ENGLISHDIR)/Bugs/pseudo-packages.description

$(ENGLISHDIR)/Bugs/pseudo-packages.description:
	wget $(CAPATH) -O $(ENGLISHDIR)/Bugs/pseudo-packages.description https://bugs.debian.org/pseudopackages/pseudo-packages.description

ifeq "$(LANGUAGE)" "en"
$(HTMLDIR)/hashbug_redirect.js: hashbug_redirect.js
	install -m 664 -p $< $(HTMLDIR)

install:: $(HTMLDIR)/hashbug_redirect.js
endif
