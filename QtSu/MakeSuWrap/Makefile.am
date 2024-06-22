CPPROGRAM=qtsuwrap

# expand pkg-config command before displaying
all:
	@echo "g++ `pkg-config --cflags --libs glib-2.0` suwrap.cpp -o $(CPPROGRAM)"
	@(g++ `pkg-config --cflags --libs glib-2.0` suwrap.cpp -o $(CPPROGRAM))

install:
	mkdir -p $(DESTDIR)$(prefix)/bin
	cp $(CPPROGRAM) $(DESTDIR)${prefix}/bin/$(CPPROGRAM)
	chown root:root $(DESTDIR)${prefix}/bin/$(CPPROGRAM)||true
	chmod ug+s $(DESTDIR)${prefix}/bin/$(CPPROGRAM)||true

uninstall:
	rm $(DESTDIR)${prefix}/bin/$(CPPROGRAM)

clean:
	rm -f $(CPPROGRAM)

distclean: clean
	rm Makefile
	rm Makefile.in
	rm -rf .deps
