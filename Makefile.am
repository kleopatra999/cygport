CLEANFILES =
EXTRA_DIST =

include $(top_srcdir)/bin/Makefile.am
include $(top_srcdir)/cygclass/Makefile.am
include $(top_srcdir)/data/Makefile.am
include $(top_srcdir)/lib/Makefile.am
include $(top_srcdir)/tests/Makefile.am
include $(top_srcdir)/tools/Makefile.am
include $(top_srcdir)/doc/Makefile.am

DISTCLEANFILES = $(PACKAGE)-$(VERSION).tar.bz2 $(PACKAGE)-$(VERSION).tar.xz

EXTRA_DIST +=				\
	AUTHORS				\
	COPYING				\
	COPYING-DOCS			\
	NEWS				\
	README				\
	TODO				\
	cygport.spec			\
	$(NULL)

dist-hook: doc/manual/cygport.1.html doc/manual/index.html
	@if test -d "$(srcdir)/.git"; \
	then \
		echo Creating ChangeLog && \
		( cd "$(top_srcdir)" && \
		  echo '# Generated by Makefile. Do not edit.'; echo; \
		  $(top_srcdir)/missing --run git log --stat --no-merges --date=short ) > ChangeLog.tmp \
		&& mv -f ChangeLog.tmp $(top_distdir)/ChangeLog \
		|| ( rm -f ChangeLog.tmp ; \
		     echo Failed to generate ChangeLog >&2 ); \
	else \
		echo A git clone is required to generate a ChangeLog >&2; \
	fi ; \
	cp -r doc/manual/ $(top_distdir)/doc/
