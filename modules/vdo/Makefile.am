## Process this file with automake to produce Makefile.in

SUBDIRS = data

VDO_MODULE_DIR = $(top_srcdir)/modules/vdo

MODULE_SO = libudisks2_vdo.so

NULL =

CPPFLAGS =                                                                     \
	-I$(top_builddir) -I$(top_srcdir)                                      \
	-DPACKAGE_LIBEXEC_DIR=\""$(libexecdir)"\"                              \
	-DPACKAGE_SYSCONF_DIR=\""$(sysconfdir)"\"                              \
	-DPACKAGE_DATA_DIR=\""$(datadir)"\"                                    \
	-DPACKAGE_BIN_DIR=\""$(bindir)"\"                                      \
	-DPACKAGE_LOCALSTATE_DIR=\""$(localstatedir)"\"                        \
	-DPACKAGE_LOCALE_DIR=\""$(localedir)"\"                                \
	-DPACKAGE_LIB_DIR=\""$(libdir)"\"                                      \
	-D_POSIX_PTHREAD_SEMANTICS -D_REENTRANT                                \
	-DUDISKS_COMPILATION                                                   \
	$(POLKIT_GOBJECT_1_CFLAGS)                                             \
	$(GLIB_CFLAGS)                                                         \
	$(GIO_CFLAGS)                                                          \
	$(GUDEV_CFLAGS)                                                        \
	$(BLOCKDEV_CFLAGS)                                                     \
	$(WARN_CFLAGS)                                                         \
	$(NULL)

BUILT_SOURCES =                                                                \
	$(NULL)

libudisks2_vdodir = $(libdir)/udisks2/modules
libudisks2_vdo_LTLIBRARIES = libudisks2_vdo.la

libudisks2_vdoincludedir = $(includedir)/udisks2/udisks

libudisks2_vdoinclude_HEADERS =                                                \
	$(top_srcdir)/modules/udisksmoduleiface.h                              \
	$(top_srcdir)/modules/udisksmoduleifacetypes.h                         \
	$(top_srcdir)/modules/udisksmoduleobject.h                             \
	$(NULL)

libudisks2_vdo_la_SOURCES =                                                    \
	$(BUILT_SOURCES)                                                       \
	$(top_srcdir)/modules/udisksmoduleiface.h                              \
	$(top_srcdir)/modules/udisksmoduleifacetypes.h                         \
	$(top_srcdir)/modules/udisksmoduleobject.h                             \
	$(top_srcdir)/modules/udisksmoduleobject.c                             \
	udiskslinuxblockvdo.h                                                  \
	udiskslinuxblockvdo.c                                                  \
	udiskslinuxmanagervdo.h                                                \
	udiskslinuxmanagervdo.c                                                \
	udisksvdotypes.h                                                       \
	udisksvdomoduleiface.c                                                 \
	$(NULL)

libudisks2_vdo_la_CPPFLAGS =                                                   \
	$(CPPFLAGS)                                                            \
	-DG_LOG_DOMAIN=\"libudisks2-vdo\"                                      \
	$(NULL)

libudisks2_vdo_la_CFLAGS =                                                     \
	$(GLIB_CFLAGS)                                                         \
	$(GIO_CFLAGS)                                                          \
	$(GUDEV_CFLAGS)                                                        \
	$(POLKIT_GOBJECT_1_CFLAGS)                                             \
	$(BLOCKDEV_CFLAGS)                                                     \
	$(NULL)

libudisks2_vdo_la_LDFLAGS =                                                    \
	-export_dynamic                                                        \
	-avoid-version                                                         \
	-module                                                                \
	-no-undefined                                                          \
	-export-symbols-regex                                                  \
	 '^udisks_.*|g_io_module_load|g_io_module_unload|g_io_module_query'    \
	$(NULL)

libudisks2_vdo_la_LIBADD =                                                     \
	$(GLIB_LIBS)                                                           \
	$(GIO_LIBS)                                                            \
	$(GUDEV_LIBS)                                                          \
	$(POLKIT_GOBJECT_1_LIBS)                                               \
	$(BLOCKDEV_LIBS)                                                       \
	$(NULL)

# ------------------------------------------------------------------------------

CLEANFILES =

EXTRA_DIST =                                                                   \
	$(NULL)

include ../Makefile.uninstalled

all-local: module_link

dist-hook:
	(for i in $(BUILT_SOURCES); do rm -f $(distdir)/$$i; done)

clean-local: module_unlink
	rm -f *~ $(BUILT_SOURCES)
