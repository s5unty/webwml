# If this makefile is not generic enough to support a translation,
# please contact debian-www.

WMLBASE=../../../..
CUR_DIR=devel/debian-nonprofit/News/2004
SUBS=

NOGENERICDEP := true

include $(WMLBASE)/Make.lang

index.$(LANGUAGE).html: index.wml $(wildcard 2004*.wml) \
                        $(wildcard 2004*.title)\
                        $(TEMPLDIR)/template.wml $(TEMPLDIR)/recent_list.wml
	$(WML) index.wml
%.$(LANGUAGE).html: %.wml $(TEMPLDIR)/news.wml
	$(WML) $(<F)
