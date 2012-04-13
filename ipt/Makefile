OPENDPI_PATH2 := ${OPENDPI_PATH}/src
OPENDPI_SRC := opendpi_cpy
OPENDPI_PRO := ${OPENDPI_SRC}/lib/protocols

CFLAGS = -fPIC -I${OPENDPI_SRC}/include -I${OPENDPI_SRC}/lib -I../src -DOPENDPI_NETFILTER_MODULE -O2 -Wall

all:
	if test -d ${OPENDPI_SRC}; then \
		cp ${OPENDPI_PATH2}/* ${OPENDPI_SRC} -R; \
	else \
		mkdir ${OPENDPI_SRC}; \
		cp ${OPENDPI_PATH2}/* ${OPENDPI_SRC} -R; \
	fi
	make libxt_opendpi.so
	rm -r ${OPENDPI_SRC}
lib%.so: lib%.o
	$(CC) -shared -o $@ $^;
lib%.o: lib%.c
	$(CC) ${CFLAGS} -D_INIT=lib$*_init -c -o $@ $<;
clean:
	rm -rf libxt_opendpi.so ${OPENDPI_SRC}
