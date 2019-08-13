LIB_NAME ?= paillier
STATIC_NAME ?= lib$(LIB_NAME).a
SHARE_NAME  ?= lib$(LIB_NAME).so

all: static_library shared_library

static_library: 
	gcc -c *.c;
	ar  -cr $(STATIC_NAME) *.o;
 
shared_library:
	gcc -shared -fpic -o $(SHARE_NAME) *.c;

install:
	mv $(STATIC_NAME) ../lib
	mv $(SHARE_NAME) ../lib

clean:
	rm -rf *.o
	rm -rf $(STATIC_NAME) $(SHARE_NAME)
