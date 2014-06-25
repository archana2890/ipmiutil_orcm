# 
# Makefile for the libintf_lanplus.a from ipmitool, but with -fPIC
#
CC = gcc
# CFLAGS = $(DEBFLAGS) -Wall -D_REENTRANT  -DLINUX -DUNIX -DUWSVR4
CFLAGS = -DHAVE_CONFIG_H -g -O2 -fno-strict-aliasing -fPIC
INCLUDES = -I. -I./inc
# LDFLAGS  = -L../

LIB_TARG   = libintf_lanplus.a
TARGETS    = $(LIB_TARG)
LIB_OBJ    = lanplus.o lanplus_strings.o lanplus_crypt.o \
		lanplus_dump.o lanplus_crypt_impl.o helper.o ipmi_strings.o
LIB_SOURCE = rmcp.h asf.h  lanplus.c lanplus.h \
		lanplus_strings.c  lanplus_crypt.c lanplus_crypt.h \
		lanplus_dump.h lanplus_dump.c \
		lanplus_crypt_impl.h lanplus_crypt_impl.c helper.c
LD_OTHER  = -lcrypto 
# -lreadline -lncurses
# -lssl

all:	$(TARGETS)

$(LIB_TARG):	$(LIB_OBJ)
	echo "ar cru $(LIB_TARG) $(LIB_OBJ)" ; \
	ar cru $(LIB_TARG) $(LIB_OBJ) 
	ranlib $(LIB_TARG)
	cp -f $(LIB_TARG) ..

clean:
	rm -f *.o *.i *.s $(TARGETS)
 
distclean:	clean

install:	$(TARGETS)
	cp -f $(LIB_TARG) ..
	
%.o:	%.c
	$(CC) -c $(CFLAGS) $(INCLUDES) -o $@ $<

