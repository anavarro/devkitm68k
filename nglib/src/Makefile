include $(NGDEV)/config.mk

ASFLAGS = -m68000 --register-prefix-optional
LDFLAGS = -Wl,-Ttext=0x0
CCFLAGS = -m68000 -O3 -Wall -fomit-frame-pointer -ffast-math -fno-builtin -I$(NGDEV)/nglib/include
ARFLAGS = cr

SOURCES  = $(wildcard *.c)
SOURCES += $(wildcard *.s)

OBJECTS = $(SOURCES:.c=.o)

LIBDIR = $(NGDEV)/nglib/lib

all: $(LIBDIR)/libng.a

$(LIBDIR)/libng.a: $(OBJECTS) 
	$(AR) $(ARFLAGS) $@ $^

%.o: %.c
	$(CC) -I$(INCDIR) $(CCFLAGS) -c $< -o $@

%.o: %.s
	$(AS) $(ASFLAGS) $< -o $@

clean:
	rm -f *.o
	rm -f libng.a

