# Makefile:
#	libpigpioj - Java (JNI) library wrapper of pigpio for the Raspberry Pi
#

TARGET=libpigpioj.so

CC	         = gcc
INCLUDE	     = -I. \
               -I/$(JAVA_HOME)/include                         \
               -I/$(JAVA_HOME)/include/linux                   \
               -I/usr/local/include -I/usr/local/include/linux

CFLAGS      := -O3 -Wall -pthread -fPIC $(INCLUDE)

LIBS         =  -Wl,-Bstatic -lpigpio -Wl,-Bdynamic -lrt

# Should not alter anything below this line
###############################################################################

SRC	=   pigpioj_util.c com_diozero_pigpioj_PigpioGpio.c com_diozero_pigpioj_PigpioI2C.c com_diozero_pigpioj_PigpioSPI.c com_diozero_pigpioj_PigpioBitBangI2C.c

OBJ =	$(SRC:.c=.o)

all:	$(TARGET)

$(TARGET):	$(OBJ)
	@echo [LINK] $(TARGET)
	@$(CC) $(OBJ) -shared -o $(TARGET) $(LIBS)

.c.o:
	@echo [COMPILE] $<
	@$(CC) -c $(CFLAGS) $< -o $@

clean:
	rm -f $(OBJ) $(TARGET) *~ core tags Makefile.bak

tags:	$(SRC)
	@echo [ctags]
	@ctags $(SRC)

depend:
	makedepend -Y $(SRC)
