
CLEANFILES = quantlib_wrap.* quantlib/QuantLibc.so .build-stamp

BUILT_SOURCES = quantlib_wrap.cpp

if HAVE_MZSCHEME
if BUILD_MZSCHEME

all-local: .build-stamp

.build-stamp: quantlib_wrap.cpp
	CXXFLAGS="$(CXXFLAGS) $(CXXWARNINGFLAGS)" $(MZSCHEME) -r setup.scm build
	touch .build-stamp

check-local: .build-stamp
	$(MZSCHEME) -r setup.scm test

install-exec-local: .build-stamp
	$(MZSCHEME) -r setup.scm install

endif
endif

quantlib_wrap.cpp: ../SWIG/*.i
	$(SWIG) -mzscheme -c++ -o quantlib_wrap.cpp ../SWIG/quantlib.i

dist-hook:
	mkdir -p $(distdir)/quantlib
	cp ./quantlib/*.ss $(distdir)/quantlib
	mkdir -p $(distdir)/examples
	cp ./examples/*.scm $(distdir)/examples
	mkdir -p $(distdir)/test
	cp ./test/*.scm $(distdir)/test

EXTRA_DIST = README.txt setup.scm $(BUILT_SOURCES)

