CC = mpicc 
CFLAGS = -Wall -c -DDEBUG
LFLAGS = -lm

OBJS = qnorm.o qfunc.o qsort.o

qnorm.o: qnorm.c
	${CC} ${CFLAGS} qnorm.c

qfunc.o: qfunc.c 
	${CC} ${CFLAGS} qfunc.c

qsort.o: qsort.c 
	${CC} ${CFLAGS} qsort.c

mpi_qnorm: ${OBJS}
	${CC} ${LFLAGS} ${OBJS} -o mpi_qnorm

all: mpi_qnorm

default_target: all

clean:
	rm -f ${OBJS}

test: mpi_qnorm
	lamboot hostnames
	cd ../../test/data ; mpirun -np 4 ../../src/mpi/mpi_qnorm -t -e=4 -g=15 -n=2 

