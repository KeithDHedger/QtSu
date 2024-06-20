#
#
AC_INIT([QtSu],[0.2.0],[PROJ],[QtSu])

AC_CONFIG_HEADERS([config.h])
AC_PROG_CXX

AM_INIT_AUTOMAKE

AC_PROG_CC

PKG_PROG_PKG_CONFIG

AC_ARG_ENABLE(gtk,[ --enable-gtk Enable GTK.],[enable_gtk=$enableval],[enable_gtk="no"])
if test $enable_gtk = "no" ;then
	QTWIDGETS_MODULES="Qt6Widgets >= 6.6.0"
	PKG_CHECK_MODULES(QTWIDGETS, $QTWIDGETS_MODULES, [got6=yes], [:])
	if test "$got6" = "yes"; then
		AC_MSG_NOTICE([Using Qt6])
		AC_DEFINE([_USEQT_], [], [Build Qt])
	else
		QTWIDGETS_MODULES="Qt5Widgets >= 5.15.0"
		PKG_CHECK_MODULES(QTWIDGETS, $QTWIDGETS_MODULES)
		AC_MSG_NOTICE([Using Qt5])
	fi

	AC_DEFINE([_USEQT_], [], [Build Qt])
	AC_SUBST(QTWIDGETS_CFLAGS)
	AC_SUBST(QTWIDGETS_LIBS)
else
	GTK_MODULES="gtk+-2.0 >= 2.24.0"
	PKG_CHECK_MODULES(GTK, $GTK_MODULES)
	AC_SUBST(GTK_CFLAGS)
	AC_SUBST(GTK_LIBS)
fi

GLIB_MODULES="glib-2.0 >= 2.34.1"
PKG_CHECK_MODULES(GLIB, $GLIB_MODULES)
AC_SUBST(GLIB_CFLAGS)
AC_SUBST(GLIB_LIBS)

AM_CONDITIONAL([KTSUSSLINK], [false],[false])

if test $enable_gtk = "no" ;then
	AC_MSG_CHECKING(create links from ktsuss and gtksu to qtsu)

	AC_ARG_ENABLE(links,[--enable-links    Create convienience symlinks from ktsuss and gtksu to qtsu.],
		[case "${enableval}" in
			yes) links=true ;;
			no)  links=false ;;
			*) AC_MSG_ERROR(bad value ${enableval} for --enable-links ) ;;
		esac],[links=false])AC_DEFINE([_USEQT_], [], [Build Qt])
	AM_CONDITIONAL([KTSUSSLINK], [test x$links = xtrue],[xfalse])
	AC_MSG_RESULT($links)
fi

AC_CHECK_FUNC(clearenv,AC_DEFINE([_GOTCLEARENV_], [],["Clear environment"]))

AC_CONFIG_FILES(Makefile QtSu/app/Makefile QtSu/MakeSuWrap/Makefile)
AC_OUTPUT
