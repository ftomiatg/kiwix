bin_PROGRAMS=kiwix-serve
AM_CPPFLAGS=-I$(top_srcdir)/src/common
AUTOMAKE_OPTIONS=subdir-objects
kiwix_serve_SOURCES= \
	kiwix-serve.cpp \
	../common/kiwix/reader.cpp \
	../common/kiwix/searcher.cpp \
	../common/kiwix/manager.cpp \
	../common/kiwix/library.cpp \
	../common/kiwix/ctpp2/CTPP2VMStringLoader.cpp \
	../common/kiwix/xapianSearcher.cpp \
	../common/base64.cpp \
	../common/pathTools.cpp \
	../common/otherTools.cpp \
	../common/regexTools.cpp \
	../common/resourceTools.cpp \
	../common/stringTools.cpp \
	../common/kiwix/reader.h \
	../common/kiwix/searcher.h \
	../common/kiwix/manager.h \
	../common/kiwix/library.h \
	../common/kiwix/ctpp2/CTPP2VMStringLoader.hpp \
	../common/kiwix/xapianSearcher.h \
	../common/base64.h \
	../common/pathTools.h \
	../common/otherTools.h \
	../common/regexTools.h \
	../common/resourceTools.h \
	../common/stringTools.h
kiwix_serve_CXXFLAGS=$(LIBZIM_CFLAGS) ${MICROHTTPD_CFLAGS} $(LIBCTPP2_CFLAGS) $(LIBPUGIXML_CFLAGS) $(XAPIAN_CFLAGS) $(ICU_CFLAGS) $(LZMA_CFLAGS) $(ZLIB_CFLAGS) -I../common/

kiwix_serve_LDFLAGS=$(CHECK_LDFLAGS)

if STATIC_BINS
kiwix_serve_LDFLAGS+= $(XAPIAN_STATIC_LDFLAGS) $(ICU_STATIC_LDFLAGS) $(MICROHTTPD_STATIC_LDFLAGS) $(LIBZIM_STATIC_LDFLAGS) $(LIBCTPP2_STATIC_LDFLAGS) $(LIBPUGIXML_STATIC_LDFLAGS) $(LZMA_STATIC_LDFLAGS) $(UUID_STATIC_LDFLAGS) $(ZLIB_STATIC_LDFLAGS) $(STATIC_LIBM_ARCHIVE) $(STATIC_LIBSTDCPP_ARCHIVE) $(STATIC_LIBDL_ARCHIVE) $(STATIC_LIBGCC_ARCHIVE) $(STATIC_LIBPTHREAD_ARCHIVE) --static
else
kiwix_serve_LDFLAGS+= $(XAPIAN_LDFLAGS) $(ICU_LDFLAGS) $(MICROHTTPD_LDFLAGS) $(LIBZIM_LDFLAGS) $(LIBCTPP2_LDFLAGS) $(LIBPUGIXML_LDFLAGS) $(LZMA_LDFLAGS) $(UUID_LDFLAGS) $(ZLIB_LDFLAGS) -lpthread
endif

if IS_OSX
# kiwix_serve_CXXFLAGS+= -stdlib=libstdc++
kiwix_serve_LDFLAGS+= $(LIBICONV_STATIC_LDFLAGS) $(GETTEXT_STATIC_LDFLAGS) -framework IOKit -framework CoreFoundation
#-static-libgcc -static-libstdc++
endif

if HAVE_UPX
all-am: all
	upx -9 $(bin_PROGRAMS)
endif
