CC=gcc
DEPS = movie.h stringlist.h movies_list_loader.h tools.h factorisation.h biblio_interface.h console_controler.h console_display.h recommendation_list.h recommendation.h
CFLAGS   = -Wall -fPIC -I.  -D REENTRANT -lwjelement -lwjreader
CFLAGS  += `gsl-config --cflags --libs`

CFLAGS  += -DGTK_DISABLE_DEPRECATED=1 -DGDK_DISABLE_DEPRECATED
CFLAGS  += -DGDK_PIXBUF_DISABLE_DEPRECATED -DG_DISABLE_DEPRECATED
CFLAGS  += -DGTK_MULTIHEAD_SAFE=1 -DGTK_MULTIDEVICE_SAFE=1
CFLAGS  += `pkg-config gtk+-3.0 --cflags`
CFLAGS  += -g

OBJ = factorisation.o factorisation_test.o tools.o
LDFLAGS  = `pkg-config gtk+-3.0 --libs`
LDFLAGS += `pkg-config gmodule-2.0 --libs`

all: interface

%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

factorisation_test: $(OBJ)
	gcc -o $@ $^ $(CFLAGS)

#testparser: movie.o stringlist.o movies_list_loader.o testparser.o tools.o
	#gcc -o $@ $^ $(CFLAGS)

#test_console_display: movie.o stringlist.o movies_list_loader.o test_console_display.o console_display.o tools.o
	#gcc -o $@ $^ $(CFLAGS)

interface_console: interface_console.o movie.o stringlist.o movies_list_loader.o console_display.o console_controler.o tools.o recommendation_list.o recommendation.o factorisation.o
	gcc -o $@ $^ $(CFLAGS)

interface: interface.o movie.o stringlist.o movies_list_loader.o console_display.o console_controler.o tools.o recommendation_list.o recommendation.o factorisation.o biblio_interface.o
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS)

clean:
	rm *.o
