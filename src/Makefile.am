## Makefile for libsigsegv/src.
## Copyright (C) 2002-2006, 2008-2011, 2016-2018, 2021-2023 Bruno Haible <bruno@clisp.org>
##
## This program is free software: you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published by
## the Free Software Foundation; either version 2 of the License, or
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

AUTOMAKE_OPTIONS = 1.5 gnits no-dependencies

RM = rm -f

lib_LTLIBRARIES = libsigsegv.la

noinst_HEADERS = \
  fault.h fault-aix3.h fault-aix3-powerpc.h fault-aix5.h fault-aix5-powerpc.h \
  fault-beos.h fault-beos-i386.h \
  fault-cygwin.h fault-cygwin-i386.h fault-cygwin-old.h \
  fault-bsd.h \
  fault-freebsd-arm.h \
  fault-freebsd-i386.h \
  fault-haiku.h fault-haiku-i386.h \
  fault-hpux.h fault-hpux-hppa.h \
  fault-hurd.h fault-hurd-i386.h fault-hurd-i386-old.h \
  fault-irix.h fault-irix-mips.h \
  fault-linux.h fault-linux-alpha.h fault-linux-alpha-old.h \
  fault-linux-arm.h fault-linux-arm-old.h \
  fault-linux-cris.h fault-linux-cris-old.h \
  fault-linux-hppa.h fault-linux-hppa-old.h \
  fault-linux-i386.h fault-linux-i386-old.h fault-linux-i386-oldold.h \
  fault-linux-ia64.h fault-linux-ia64-old.h \
  fault-linux-loongarch.h \
  fault-linux-m68k.h fault-linux-m68k-old.h fault-linux-m68k-old.c \
  fault-linux-mips.h fault-linux-mips-old.h \
  fault-linux-nds32.h \
  fault-linux-powerpc.h fault-linux-powerpc-old.h \
  fault-linux-riscv64.h \
  fault-linux-s390.h fault-linux-s390-old.h \
  fault-linux-sh.h fault-linux-sh-old.h \
  fault-linux-sparc.h fault-linux-sparc-old.h \
  fault-linux-x86_64-old.h \
  fault-macos.h fault-macos-arm64.h fault-macos-i386.h fault-macos-powerpc.h \
  fault-macos-i386-old.h \
  fault-macosdarwin5-powerpc.h fault-macosdarwin5-powerpc.c \
  fault-macosdarwin7-powerpc.h fault-macosdarwin7-powerpc.c \
  fault-netbsd.h fault-netbsd-alpha.h fault-netbsd-alpha.c \
  fault-none.h \
  fault-openbsd.h fault-openbsd-alpha.h fault-openbsd-arm.h \
  fault-openbsd-hppa.h fault-openbsd-i386.h fault-openbsd-m68k.h \
  fault-openbsd-m88k.h fault-openbsd-mips.h fault-openbsd-powerpc.h \
  fault-openbsd-sh.h fault-openbsd-sparc.h fault-openbsd-vax.h \
  fault-osf.h fault-osf-alpha.h \
  fault-posix.h fault-posix-ucontext.h \
  fault-solaris.h fault-solaris-i386.h fault-solaris-sparc.h fault-solaris11-sparc.h \
  machfault.h machfault-macos.h \
  signals.h signals-bsd.h signals-hpux.h signals-hurd.h signals-macos.h \
  leave.h \
  stackvma.h

EXTRA_DIST = \
  handler-none.c handler-unix.c handler-macos.c handler-win32.c \
  stackvma-none.c stackvma-simple.c stackvma-linux.c stackvma-freebsd.c \
  stackvma-netbsd.c stackvma-aix.c stackvma-procfs.c stackvma-cygwin.c \
  stackvma-beos.c stackvma-mach.c stackvma-mquery.c \
  stackvma-mincore.c stackvma-rofile.c stackvma-vma-iter.c \
  leave-none.c leave-nop.c leave-sigaltstack.c leave-setcontext.c

AM_CPPFLAGS = -I. -I$(srcdir)
DEFS = @DEFS@

libsigsegv_la_SOURCES = handler.c stackvma.c leave.c dispatcher.c version.c

libsigsegv_la_LDFLAGS = \
  -rpath $(libdir) \
  -version-info $(LIBSIGSEGV_VERSION_INFO) \
  -lc -no-undefined

# Before making a release, change this according to the libtool documentation,
# section "Library interface versions".
LIBSIGSEGV_VERSION_INFO = 2:7:0

# Dependencies.
handler.$(OBJEXT) : ../config.h sigsegv.h @CFG_HANDLER@ $(noinst_HEADERS) 
stackvma.$(OBJEXT) : ../config.h @CFG_STACKVMA@ stackvma.h
leave.$(OBJEXT) : ../config.h @CFG_LEAVE@
dispatcher.$(OBJEXT) : sigsegv.h


# Special rules for installing sigsegv.h.

install-data-local:
	$(mkinstalldirs) $(DESTDIR)$(includedir)
	$(INSTALL_DATA) sigsegv.h $(DESTDIR)$(includedir)/sigsegv.h

installdirs-local:
	$(mkinstalldirs) $(DESTDIR)$(includedir)

uninstall-local:
	$(RM) $(DESTDIR)$(includedir)/sigsegv.h


DISTCLEANFILES = sigsegv.h
