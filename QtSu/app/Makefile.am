
AUTOMAKE_OPTIONS = subdir-objects

include ../flagsandlibs
include ../sources

qtsu_SOURCES = $(COMMONSRC)

bin_PROGRAMS = qtsu

man1_MANS = ../resources/man/qtsu.1
  
if KTSUSSLINK
links = "makelink"
endif
     
install-exec-hook:
	if [ x${links} = xmakelink ];then ln -sfv qtsu $(DESTDIR)${prefix}/bin/ktsuss;ln -sfv qtsu $(DESTDIR)${prefix}/bin/gtksu;fi


