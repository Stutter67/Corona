## Makefile.am: produce Makefile.in from this

## copyright by the mpg123 project - free software under the terms of the LGPL 2.1
## see COPYING and AUTHORS files in distribution or http://mpg123.org
## initially written by Nicholas J. Humfrey

AM_CPPFLAGS = -DPKGLIBDIR="\"$(pkglibdir)\""
mpg123_LDADD = $(LIBLTDL) libmpg123/libmpg123.la @MODULE_OBJ@ @OUTPUT_OBJ@ @OUTPUT_LIBS@
mpg123_LDFLAGS = @EXEC_LT_LDFLAGS@ @OUTPUT_LDFLAGS@
# Just mpg123_INCLUDES has no effect on build! Trying that before reverting to AM_CPPFLAGS.
INCLUDES = $(LTDLINCL) -I$(top_builddir)/src/libmpg123 -I$(top_srcdir)/src/libmpg123
# libltdl is not mentioned here... it's not that trivial
mpg123_DEPENDENCIES = @OUTPUT_OBJ@ @MODULE_OBJ@ libmpg123/libmpg123.la

SUBDIRS = output libmpg123
EXTRA_DIST = legacy_module.c module.c sfifo.c sfifo.h


CLEANFILES = *.a

bin_PROGRAMS = mpg123

EXTRA_PROGRAMS = tests/seek_accuracy tests/seek_whence tests/noise tests/text tests/plain_id3

mpg123_SOURCES = \
	audio.c \
	audio.h \
	buffer.c \
	buffer.h \
	common.c \
	common.h \
	libmpg123/compat.c \
	libmpg123/compat.h \
	control_generic.c \
	equalizer.c \
	getlopt.c \
	getlopt.h \
	httpget.c \
	httpget.h \
	resolver.c \
	resolver.h \
	genre.h \
	genre.c \
	module.h \
	mpg123.c \
	mpg123app.h \
	metaprint.c \
	metaprint.h \
	local.h \
	local.c \
	playlist.c \
	playlist.h \
	streamdump.h \
	streamdump.c \
	term.c \
	term.h \
	wav.c \
	win32_support.h \
	wavhead.h \
	xfermem.c \
	xfermem.h

if WIN32_CODES
mpg123_SOURCES += \
	win32_support.c \
	win32_net.c
endif

# That is not nice... but it is how I manage to get the dependency on output/alsa.o without error about .deps/output/alsa.Tpo .
# Did I mention that recursive make sucks?
# `%'-style pattern rules are a GNU make extension
#find output/ -name '*.c' | perl -ne 'chomp; $mod=$_; $mod=~s/\.c$/.\$(OBJEXT)/;
#print "$mod: $_ audio.h module.h\n";
#print "\tcd output && \$(MAKE)\n\n";'

output/coreaudio.$(OBJEXT): output/coreaudio.c audio.h module.h
	cd output && $(MAKE)

output/win32.$(OBJEXT): output/win32.c audio.h module.h
	cd output && $(MAKE)

output/alsa05.$(OBJEXT): output/alsa05.c audio.h module.h
	cd output && $(MAKE)

output/sdl.$(OBJEXT): output/sdl.c audio.h module.h
	cd output && $(MAKE)

output/dummy.$(OBJEXT): output/dummy.c audio.h module.h
	cd output && $(MAKE)

output/alib.$(OBJEXT): output/alib.c audio.h module.h
	cd output && $(MAKE)

output/libao.$(OBJEXT): output/libao.c audio.h module.h
	cd output && $(MAKE)

output/sun.$(OBJEXT): output/sun.c audio.h module.h
	cd output && $(MAKE)

output/aix.$(OBJEXT): output/aix.c audio.h module.h
	cd output && $(MAKE)

output/oss.$(OBJEXT): output/oss.c audio.h module.h
	cd output && $(MAKE)

output/mint.$(OBJEXT): output/mint.c audio.h module.h
	cd output && $(MAKE)

output/pulse.$(OBJEXT): output/pulse.c audio.h module.h
	cd output && $(MAKE)

output/jack.$(OBJEXT): output/jack.c audio.h module.h
	cd output && $(MAKE)

output/os2.$(OBJEXT): output/os2.c audio.h module.h
	cd output && $(MAKE)

output/nas.$(OBJEXT): output/nas.c audio.h module.h
	cd output && $(MAKE)

output/sgi.$(OBJEXT): output/sgi.c audio.h module.h
	cd output && $(MAKE)

output/portaudio.$(OBJEXT): output/portaudio.c audio.h module.h
	cd output && $(MAKE)

output/arts.$(OBJEXT): output/arts.c audio.h module.h
	cd output && $(MAKE)

output/esd.$(OBJEXT): output/esd.c audio.h module.h
	cd output && $(MAKE)

output/alsa.$(OBJEXT): output/alsa.c audio.h module.h
	cd output && $(MAKE)

output/hp.$(OBJEXT): output/hp.c audio.h module.h
	cd output && $(MAKE)

output/sndio.$(OBJEXT): output/sndio.c audio.h module.h
	cd output && $(MAKE)


# Would have to mention _all_ source files... Dammit, that's what the libmpg123/Makefile.am does!
# But again, the a make $something here needs that stupid rule... WHY???
libmpg123/libmpg123.la: config.h libmpg123/mpg123.h
	cd libmpg123 && $(MAKE)

tests_seek_accuracy_SOURCES = \
tests/seek_accuracy.c \
libmpg123/compat.h \
libmpg123/compat.c

tests_seek_accuracy_DEPENDENCIES = libmpg123/libmpg123.la
tests_seek_accuracy_LDADD = libmpg123/libmpg123.la

tests_seek_whence_SOURCES = \
tests/seek_whence.c \
libmpg123/compat.h \
libmpg123/compat.c

tests_seek_whence_DEPENDENCIES = libmpg123/libmpg123.la
tests_seek_whence_LDADD = libmpg123/libmpg123.la

tests_noise_SOURCES = \
tests/noise.c \
libmpg123/compat.h \
libmpg123/compat.c \
libmpg123/dither.h \
libmpg123/dither.c

tests_text_SOURCES = \
tests/text.c \
tests/testtext.h \
libmpg123/compat.h \
libmpg123/compat.c

tests_text_DEPENDENCIES = libmpg123/libmpg123.la
tests_text_LDADD = libmpg123/libmpg123.la

tests_plain_id3_SOURCES = \
tests/plain_id3.c \
libmpg123/compat.h \
libmpg123/compat.c

tests_plain_id3_DEPENDENCIES = libmpg123/libmpg123.la
tests_plain_id3_LDADD = libmpg123/libmpg123.la
