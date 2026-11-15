
CROSSPREFIX=/opt/cross-mint/bin/m68k-atari-mint-
PATH = /opt/cross-mint/m68k-atari-mint/bin:/opt/cross-mint/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin
LD_LIBRARY_PATH=/opt/cross-mint/lib:/opt/cross-mint/m68k-atari-mint/lib:$LD_LIBRARY_PATH
DESTDIR=/opt/cross-mint/m68k-atari-mint

CC = $(CROSSPREFIX)gcc
AS = $(CC)
AR = $(CROSSPREFIX)ar
RANLIB = $(CROSSPREFIX)ranlib
STRIP = $(CROSSPREFIX)strip
FLAGS = $(CROSSPREFIX)flags

CFLAGS = -I../include -I. -W

OFLAGS = -Wall -O2 -fomit-frame-pointer -Wno-sign-compare -Wno-missing-field-initializers -Wno-cast-function-type \
         -DPLUTOSVG_BUILD_STATIC #-DPLUTOSVG_HAS_FREETYPE

OBJS = plutosvg.c

libplutosvg.a:
	mkdir -p ../lib
	mkdir -p ../lib/m68020-60
	mkdir -p ../lib/m5475

	$(CC) $(CFLAGS) -m68000 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libplutosvg.a $(DESTDIR)/lib/libplutosvg.a
	cp libplutosvg.a ../lib/libplutosvg.a
	rm -f *.o libplutosvg.a
	$(CC) $(CFLAGS) -m68020-60 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libplutosvg.a $(DESTDIR)/lib/m68020-60/libplutosvg.a
	cp libplutosvg.a ../lib/m68020-60/libplutosvg.a
	rm -f *.o libplutosvg.a
	$(CC) $(CFLAGS) -mcpu=5475 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libplutosvg.a $(DESTDIR)/lib/m5475/libplutosvg.a
	cp libplutosvg.a ../lib/m5475/libplutosvg.a
	rm -f *.o libplutosvg.a

clean:
	rm -f ../lib/libplutosvg.a
	rm -f ../lib/m68020-60/libplutosvg.a
	rm -f ../lib/m5475/libplutosvg.a
	rm -f *.o libplutosvg.a
