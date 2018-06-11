all: libws2812.a

CPU             = msp430g2553
CFLAGS          = -mmcu=${CPU} 
LDFLAGS		= -L/opt/ti/msp430_gcc/include

#switch the compiler (for the internal make rules)
CC              = msp430-elf-gcc
AS              = msp430-elf-as
AR              = msp430-elf-ar

libws2812.a: ws2812.o
	$(AR) crs $@ $^

install: libws2812.a
	mkdir -p ../h ../lib
	mv $^ ../lib
	cp *.h ../h

clean:
	rm -f libws2812.a *.o

demo.elf: demo.o ws2812.o
	${CC} ${CFLAGS} ${LDFLAGS} -o $@ $^

load: demo.elf
	mspdebug rf2500 "prog demo.elf"
