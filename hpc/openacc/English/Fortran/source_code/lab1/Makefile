# Copyright (c) 2020 NVIDIA Corporation.  All rights reserved. 
FC := nvfortran
ACCFLAGS_1 := -fast
ACCFLAGS_2 := -fast -ta=multicore -Minfo=accel
ACCFLAGS_3 := -fast -ta=tesla:managed -Minfo=accel


all: laplace_serial laplace_multicore

laplace_serial: laplace2d.serial.f90 jacobi.f90 
	cp           laplace2d.serial.f90 laplace2d.f90
	${FC} ${ACCFLAGS_1} -o laplace_serial laplace2d.f90 jacobi.f90

laplace_multicore: solutions/laplace2d.parallel.f90 jacobi.f90 
	cp solutions/laplace2d.parallel.f90 laplace2d.f90
	${FC} ${ACCFLAGS_2} -o laplace_multicore laplace2d.f90 jacobi.f90 

laplace_gpu: solutions/laplace2d.gpu.f90 jacobi.f90 
	cp solutions/laplace2d.gpu.f90 laplace2d.f90
	${FC} ${ACCFLAGS_3} -o laplace_gpu laplace2d.f90 jacobi.f90 

clean:
	rm -f *.o laplace_*
