OPENDPI_SRC := ../../src
OPENDPI_PRO := ${OPENDPI_SRC}/lib/protocols

CFLAGS = -Werror -DDEBUG -fPIC -I${OPENDPI_SRC}/include -I${OPENDPI_SRC}/lib -I../src -DOPENDPI_NETFILTER_MODULE -O2 -Wall

all:
	make libxt_opendpi.so
lib%.so: lib%.o
	$(CC) -shared -o $@ $^;
lib%.o: lib%.c
	$(CC) ${CFLAGS} -D_INIT=lib$*_init -c -o $@ $<;
clean:
	rm -rf libxt_opendpi.so
