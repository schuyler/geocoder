all: libsqlite3_geocoder.so
CC=gcc
CFLAGS=-fPIC -O2 -Wall

libsqlite3_geocoder.so: extension.o wkb_compress.o util.o metaphon.o levenshtein.o
	$(CC) $(CFLAGS) -I/usr/include -shared $^ -o $@ -lm -lsqlite3 

test: test_wkb_compress test_levenshtein

test_wkb_compress: wkb_compress.c
	$(CC) -DTEST -o wkb_compress $^

test_levenshtein: levenshtein.c
	$(CC) -DTEST -o levenshtein $^

clean:
	rm -f *.o *.so wkb_compress levenshtein
