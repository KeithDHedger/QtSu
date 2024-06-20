
include ../flagsandlibs

qtsuwrap_SOURCES = suwrap.cpp

bin_PROGRAMS = qtsuwrap

install-exec-hook:
	chown root:root $(DESTDIR)${prefix}/bin/qtsuwrap||true
	chmod ug+s $(DESTDIR)${prefix}/bin/qtsuwrap||true
