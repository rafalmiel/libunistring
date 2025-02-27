## Makefile for the lib subdirectory of GNU libunistring.
## Copyright (C) 2009-2025 Free Software Foundation, Inc.
##
## This program is free software: you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published by
## the Free Software Foundation; either version 3 of the License, or
## (at your option) any later version.
##
## This program is distributed in the hope that it will be useful,
## but WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.
##
## You should have received a copy of the GNU General Public License
## along with this program.  If not, see <https://www.gnu.org/licenses/>.

## Process this file with automake to produce Makefile.in.

AUTOMAKE_OPTIONS = 1.5 gnits subdir-objects no-dependencies
EXTRA_DIST =
BUILT_SOURCES =
MOSTLYCLEANFILES = core *.stackdump
MOSTLYCLEANDIRS =
CLEANFILES =
DISTCLEANFILES =
MAINTAINERCLEANFILES =
SUFFIXES =

lib_LTLIBRARIES = libunistring.la

nodist_include_HEADERS = \
  unitypes.h \
  unistr.h \
  uniconv.h \
  unistdio.h \
  uniname.h \
  unictype.h \
  uniwidth.h \
  unigbrk.h \
  uniwbrk.h \
  unilbrk.h \
  unimetadata.h \
  uninorm.h \
  unicase.h

nobase_include_HEADERS = \
  unistring/inline.h

noinst_HEADERS = \
  unistring-notinline.h

AM_CPPFLAGS = \
  -I. -I$(srcdir) \
  -I$(top_builddir) -I$(top_srcdir) \
  -DIN_LIBUNISTRING

# Rules generated and collected by gnulib-tool.
include Makefile.gnulib

# Additional source files.
libunistring_la_SOURCES += version.c

# The <stdint.h> replacement that can be installed.
nobase_nodist_include_HEADERS = \
  unistring/stdint.h

# Produce an unistring/stdint.h that is not compiler dependent.
# Glibc >= 2 has <stdint.h>.
# GCC >= 4.5 provides <stdint.h>, see https://gcc.gnu.org/gcc-4.5/changes.html.
# On most other platforms that have it, it is buggy in one way or the other.
unistring/stdint.h : $(STDINT_H) stdint.mini.h
	@MKDIR_P@ unistring
	rm -f $@-t $@
	{ echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */'; \
	  echo '#include <stddef.h>'; \
	  echo '#if __GLIBC__ >= 2'; \
	  echo '#include <stdint.h>'; \
	  echo '#else'; \
	  if test -f /usr/include/stdint.h; then \
	    HAVE_STDINT_H='1'; \
	  else \
	    HAVE_STDINT_H='defined __MINGW32__ || defined __HAIKU__ || ((__GNUC__ > 4 || (__GNUC__ == 4 && __GNUC_MINOR__ >= 5)) && !defined __NetBSD__)'; \
	  fi; \
	  if test -f /usr/include/inttypes.h; then \
	    HAVE_INTTYPES_H='1'; \
	  else \
	    HAVE_INTTYPES_H='defined __MINGW32__ || defined __HAIKU__'; \
	  fi; \
	  if test -f /usr/include/sys/inttypes.h; then \
	    HAVE_SYS_INTTYPES_H='1'; \
	  else \
	    HAVE_SYS_INTTYPES_H='0'; \
	  fi; \
	  sed_escape_ampersands='s/&/\\&/g'; \
	  HAVE_STDINT_H=`echo "$$HAVE_STDINT_H" | sed -e "$$sed_escape_ampersands"`; \
	  sed -e 's/@''HAVE_STDINT_H''@/'"$$HAVE_STDINT_H"'/g' \
	      -e 's|@''INCLUDE_NEXT''@|include|g' \
	      -e 's|@''PRAGMA_SYSTEM_HEADER''@||g' \
	      -e 's|@''NEXT_STDINT_H''@|<stdint.h>|g' \
	      -e 's/@''HAVE_SYS_TYPES_H''@/1/g' \
	      -e 's/@''HAVE_INTTYPES_H''@/'"$$HAVE_INTTYPES_H"'/g' \
	      -e 's/@''HAVE_SYS_INTTYPES_H''@/'"$$HAVE_SYS_INTTYPES_H"'/g' \
	      -e 's/@''HAVE_SYS_BITYPES_H''@/0/g' \
	      < $(srcdir)/stdint.mini.h; \
	  echo '#endif'; \
	} > $@-t
	mv $@-t $@
BUILT_SOURCES    += unistring/stdint.h
MOSTLYCLEANFILES += unistring/stdint.h-t
CLEANFILES       += unistring/stdint.h
EXTRA_DIST       += stdint.mini.h

# localcharset.h is not public, but its contents is documented.
nobase_nodist_include_HEADERS += unistring/localcharset.h
unistring/localcharset.h : localcharset.h
	@MKDIR_P@ unistring
	rm -f $@-t $@
	cp $(srcdir)/localcharset.h $@-t
	mv $@-t $@
BUILT_SOURCES    += unistring/localcharset.h
MOSTLYCLEANFILES += unistring/localcharset.h-t
CLEANFILES       += unistring/localcharset.h

# iconveh.h is not public, but its contents is documented.
nobase_nodist_include_HEADERS += unistring/iconveh.h
unistring/iconveh.h : iconveh.h
	@MKDIR_P@ unistring
	rm -f $@-t $@
	cp $(srcdir)/iconveh.h $@-t
	mv $@-t $@
BUILT_SOURCES    += unistring/iconveh.h
MOSTLYCLEANFILES += unistring/iconveh.h-t
CLEANFILES       += unistring/iconveh.h

# unistring/version.h is public.
nobase_nodist_include_HEADERS += unistring/version.h

# unistring/cdefs.h is not public, but is included by other header files.
nobase_include_HEADERS += unistring/cdefs.h

# unistring/woe32dll.h is not public, but is included by other header files.
nobase_nodist_include_HEADERS += unistring/woe32dll.h

# Directories that contain some CLEANFILES.
CLEANDIRS =
CLEANDIRS_NOT_IN_SRCDIR = unistring
clean-local: clean-generic
	@for dir in '' $(CLEANDIRS); do \
	  if test -n "$$dir" && test -d $$dir; then \
	    echo "rmdir $$dir"; rmdir $$dir; \
	  fi; \
	done; \
	if test '$(srcdir)' != '.'; then \
	  for dir in '' $(CLEANDIRS_NOT_IN_SRCDIR); do \
	    if test -n "$$dir" && test -d $$dir; then \
	      echo "rmdir $$dir"; rmdir $$dir; \
	    fi; \
	  done; \
	fi; \
        :

# Directories that contain some DISTCLEANFILES.
DISTCLEANDIRS = sys
DISTCLEANDIRS_NOT_IN_SRCDIR =
distclean-local: distclean-generic
	@for dir in '' $(DISTCLEANDIRS); do \
	  if test -n "$$dir" && test -d $$dir; then \
	    echo "rmdir $$dir"; rmdir $$dir; \
	  fi; \
	done; \
	if test '$(srcdir)' != '.'; then \
	  for dir in '' $(DISTCLEANDIRS_NOT_IN_SRCDIR); do \
	    if test -n "$$dir" && test -d $$dir; then \
	      echo "rmdir $$dir"; rmdir $$dir; \
	    fi; \
	  done; \
	fi; \
        :

# List of header files that get installed and that declare 'extern' symbols.
HEADERS_WITH_EXTERNS = \
  unitypes.h \
  unistr.h \
  uniconv.h \
  unistdio.h \
  uniname.h \
  unictype.h \
  uniwidth.h \
  unigbrk.h \
  uniwbrk.h \
  unilbrk.h \
  unimetadata.h \
  uninorm.h \
  unicase.h \
  localcharset.h \
  iconveh.h \
  unistring/version.in.h

# List of exported symbols.
# We extract it from the header files that get installed.
# We keep symbols that start with "_UC", because they may be needed for
# compiling newer versions of gnulib modules when the gnulib module
# 'libunistring-optional' is in use.
# This file has the same format as the one expected by the libtool option
# '-export-symbols', but we don't use this option, because it would prevent us
# from building some of the gnulib unit tests.
$(srcdir)/libunistring.sym : $(HEADERS_WITH_EXTERNS)
	if \
	  for f in $(HEADERS_WITH_EXTERNS); do \
	    if test -f $$f; then \
	      cat $$f; \
	    else \
	      cat $(srcdir)/$$f; \
	    fi; \
	  done \
	  | $(srcdir)/declared.sh > $@-t1; \
	then \
	  LC_ALL=C sort < $@-t1 | LC_ALL=C uniq > $@-t2 && mv $@-t2 $@; \
	else \
	  if test -f $@; then \
	    echo "Continuing with existing libunistring.sym."; \
	  else \
	    exit 1; \
	  fi; \
	fi
# We distribute it because declared.sh relies on GNU sed.
# The GNU Coding Standards say in
# <https://www.gnu.org/prep/standards/html_node/Makefile-Basics.html>:
#   "GNU distributions usually contain some files which are not source files
#    ... . Since these files normally appear in the source directory, they
#    should always appear in the source directory, not in the build directory.
#    So Makefile rules to update them should put the updated files in the
#    source directory."
# Therefore we put this file in the source directory, not the build directory.
MOSTLYCLEANFILES     += libunistring.sym-t1 libunistring.sym-t2
MAINTAINERCLEANFILES += libunistring.sym
EXTRA_DIST           += libunistring.sym declared.sh

# Tell the mingw or Cygwin linker which symbols to export.
if WOE32DLL
libunistring_la_SOURCES += ../woe32dll/unistring-exports.c
libunistring_la_LDFLAGS += -Wl,--export-all-symbols
endif

# Hide undesired symbols that are defined by libunistring_la_SOURCES or
# libunistring_la_LIBADD from the global namespace, by prefixing them with
# "libunistring_".
# But don't hide symbols that start with "libintl_locale", for the reason
# stated in localename-table.h.
all check install: config.h
config.h: $(BUILT_SOURCES) $(srcdir)/libunistring.sym
	{ echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */'; \
	  : "Avoid double inclusion, to avoid a warning about redefinitions."; \
	  echo '#ifndef UNISTRING_CONFIG_H'; \
	  echo '#define UNISTRING_CONFIG_H'; \
	  echo; \
	  echo '#include "../config.h"'; \
	  echo; \
	  echo '#endif /* UNISTRING_CONFIG_H */'; \
	} > config.h && \
	if test -n "$(NAMESPACING)" && test -n "$(HAVE_GLOBAL_SYMBOL_PIPE)"; then \
	  { \
	    { \
	      for f in $(libunistring_la_SOURCES) $(libunistring_la_LIBADD); do \
	        case $$f in \
	          *.res.lo ) ;; \
	          *.c | *.$(OBJEXT) | *.lo ) \
	            sf=`echo "$$f" | sed -e 's,^libunistring_la-,,' -e 's,\\.[^.]*$$,,'`.c; \
	            test -f $$sf || sf=$(srcdir)/$$sf; \
	            of=`echo "$$f" | sed -e 's,^.*/,,' -e 's,^libunistring_la-,,' -e 's,\\.[^.]*$$,,'`.$(OBJEXT); \
	            echo "$(COMPILE) -c $$sf" 1>&6; \
	            $(COMPILE) -c $$sf || { rm -f config.h; exit 1; }; \
	            sh ./exported.sh $$of 1>&5; \
	            rm -f $$of `echo "$$of" | sed -e 's,\\.$(OBJEXT)$$,.lo,'`; \
	            ;; \
	        esac; \
	      done; \
	    } 5>&1 1>&2 \
	      | sed -e 's,.* ,,' | grep -v '@' | LC_ALL=C sort | LC_ALL=C uniq \
	      | LC_ALL=C $(top_srcdir)/build-aux/join-v-1 - $(srcdir)/libunistring.sym \
	      | grep -v '^libintl_locale' \
	      | grep -v 'gl_get_setlocale_null_lock' \
	      | sed -e 's,^\(.*\)$$,#define \1 libunistring_\1,' > config.h-t; \
	  } 6>&1 && \
	  if test -f config.h; then \
	    cat config.h-t >> config.h; \
	    rm -f config.h-t; \
	  else \
	    rm -f config.h-t; \
	    exit 1; \
	  fi \
	fi
MOSTLYCLEANFILES += config.h config.h-t

# Version information according to Woe32 conventions.
EXTRA_DIST += libunistring.rc
if WOE32
WOE32_LIBADD = libunistring.res.lo
libunistring.res.lo : $(srcdir)/libunistring.rc
	$(LIBTOOL) --tag=RC $(AM_LIBTOOLFLAGS) $(LIBTOOLFLAGS) --mode=compile $(RC) `$(SHELL) $(top_srcdir)/build-aux/windres-options --escape $(VERSION)` -i $(srcdir)/libunistring.rc -o libunistring.res.lo --output-format=coff
MOSTLYCLEANFILES += libunistring.res.lo
else
WOE32_LIBADD =
endif
libunistring_la_LIBADD       += $(WOE32_LIBADD)
libunistring_la_DEPENDENCIES += $(WOE32_LIBADD)

# Parametrization of the 'relocatable-lib-lgpl' module.
AM_CPPFLAGS += -DDEPENDS_ON_LIBICONV=1

# Libtool's library version information for libunistring.
# See the libtool documentation, section "Library interface versions".
LTV_CURRENT=7
LTV_REVISION=0
LTV_AGE=2

# How to build libunistring.la.
libunistring_la_LDFLAGS += \
  -version-info $(LTV_CURRENT):$(LTV_REVISION):$(LTV_AGE) \
  -rpath $(libdir)
