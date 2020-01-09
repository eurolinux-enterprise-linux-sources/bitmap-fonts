INSTALLDIR=/usr/share/fonts/bitmap-fonts
VERSION=0.3

BDFFONTS=					\
	4x6.bdf					\
	5x7.bdf					\
	5x8.bdf					\
	6x9.bdf					\
	6x10.bdf				\
	6x12.bdf				\
	6x13.bdf				\
	6x13B.bdf				\
	7x14.bdf				\
	7x14B.bdf				\
	9x15.bdf				\
	9x15B.bdf				\
	9x18B.bdf				\
	9x18.bdf				\
	10x20.bdf				\
	lutBS08.bdf				\
	lutBS10.bdf				\
	lutBS12.bdf				\
	lutBS14.bdf				\
	lutBS18.bdf				\
	lutBS19.bdf				\
	lutBS24.bdf				\
	lutRS08.bdf				\
	lutRS10.bdf				\
	lutRS12.bdf				\
	lutRS14.bdf				\
	lutRS18.bdf				\
	lutRS19.bdf				\
	lutRS24.bdf				\
	fangsongti16.bdf			\
	fangsongti24.bdf

PCFFONTS=$(BDFFONTS:.bdf=.pcf)

pcf: $(PCFFONTS)

install: pcf
	mkdir -p $(DESTDIR)$(INSTALLDIR)
	for i in $(PCFFONTS) ; do \
		install -m 0644 $$i $(DESTDIR)$(INSTALLDIR) ; \
	done

dist:
	rm -rf bitmap-fonts-$(VERSION)
	mkdir bitmap-fonts-$(VERSION)
	for i in *.bdf README LU_LEGALNOTICE Makefile ; do  \
		cp $$i bitmap-fonts-$(VERSION) ; \
	done
	tar cvf - bitmap-fonts-$(VERSION) | bzip2 -c > bitmap-fonts-$(VERSION).tar.bz2
	rm -rf bitmap-fonts-$(VERSION)

clean:
	rm -f *.pcf

all: pcf

%.pcf: %.bdf
	sed 's/\<Fixed\>/MiscFixed/' < $< > $<.tmp && bdftopcf $<.tmp > $@ && rm $<.tmp || ( rm $<.tmp $@ && false )

.PHONY: install all pcf
