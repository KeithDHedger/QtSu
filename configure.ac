#
#
AC_INIT([QtSu],[0.2.1],[PROJ],[QtSu])

AC_CONFIG_HEADERS([config.h])
AC_PROG_CXX

AM_INIT_AUTOMAKE

AC_PROG_CC

PKG_PROG_PKG_CONFIG

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

AC_SUBST(QTWIDGETS_CFLAGS)
AC_SUBST(QTWIDGETS_LIBS)

GLIB_MODULES="glib-2.0 >= 2.34.1"
PKG_CHECK_MODULES(GLIB, $GLIB_MODULES)
AC_SUBST(GLIB_CFLAGS)
AC_SUBST(GLIB_LIBS)

AM_CONDITIONAL([KTSUSSLINK], [false],[false])

AC_MSG_CHECKING(whether to create links)
AC_ARG_ENABLE(links,AS_HELP_STRING([--enable-links],[Create Links]),
    [enable_links=$enableval],
    [enable_links="yes"])
AC_MSG_RESULT($enable_links)
if test "$enable_links" = "yes"; then
	AM_CONDITIONAL([KTSUSSLINK], [ true],[false])
fi

AC_CHECK_FUNC(clearenv,AC_DEFINE([_GOTCLEARENV_], [],["Clear environment"]))

AC_CONFIG_FILES(Makefile QtSu/app/Makefile QtSu/MakeSuWrap/Makefile)
AC_OUTPUT
