
AUTOMAKE_OPTIONS = subdir-objects

include ../flagsandlibs
include ../sources

qtsu_SOURCES = $(COMMONSRC)

bin_PROGRAMS = qtsu

man1_MANS = ../resources/man/qtsu.1
  
if KTSUSSLINK
ktsuss = "makelink"
endif
     
install-exec-hook:
	if [ x${ktsuss} = xmakelink ];then ln -sfv qtsu $(DESTDIR)${prefix}/bin/ktsuss;fi


