SRCS+= protocol.c
SRCS+= engine.c
SRCS+= bootimg_utils.cpp
SRCS+= fastboot.c
SRCS+= usb_linux.c
SRCS+= util_linux.c
SRCS+= util.c

VPATH+= ../libsparse
SRCS+= backed_block.c
SRCS+= output_file.c
SRCS+= sparse.c
SRCS+= sparse_crc32.c
SRCS+= sparse_err.c
SRCS+= sparse_read.c

#VPATH+= ../../extras/ext4_utils
#SRCS+= allocate.c
#SRCS+= contents.c
#SRCS+= ext4_utils.c
#SRCS+= extent.c
#SRCS+= indirect.c
#SRCS+= make_ext4fs.c
#SRCS+= sha1.c
#SRCS+= uuid.c
#SRCS+= wipe.c

CPPFLAGS+= -DADB_HOST=1
CPPFLAGS+= -DHAVE_FORKEXEC=1
CPPFLAGS+= -DHAVE_SYMLINKS
CPPFLAGS+= -DHAVE_TERMIO_H
CPPFLAGS+= -D_GNU_SOURCE
CPPFLAGS+= -D_XOPEN_SOURCE
CPPFLAGS+= -DFASTBOOT_REVISION=\"999\"
CPPFLAGS+= -I.
CPPFLAGS+= -I../include
CPPFLAGS+= -I../libsparse/include
CPPFLAGS+= -I../mkbootimg
CPPFLAGS+= -I../../extras/ext4_utils

CFLAGS+= $(RPM_OPT_FLAGS)
#LIBS= -lrt -lpthread -lz -lselinux
LIBS= -lrt -lpthread -lz

CC= $(TOOLCHAIN)gcc
LD= $(TOOLCHAIN)gcc

OBJS= $(SRCS:.c=.o)

all: fastboot

fastboot: $(OBJS)
	$(LD) -o $@ $(LDFLAGS) $(OBJS) $(LIBS)

install: fastboot
	install fastboot $(DESTDIR)$(BINDIR)

clean:
	rm -rf $(OBJS)
