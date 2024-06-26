CC = mpicc
CU = nvcc
FC = mpif90
CFLAGS += -O3
FFLAGS += -O3 -Wl,-z,noexecstack
CUFLAGS += -O3

.PHONY: all

all: stencil2d-openacc            \
     stencil2d-cuda               \
     stencil2d-cuda-double        \
     stencil2d-cuda-thread-halo   \
     stencil2d-cuda-reduce-arrays \
     stencil2d-cuda-merge-kernels \
     stencil2d-cuda-basic

stencil2d-cuda:
	$(CU) $(CUFLAGS) stencil2d.cu utils.cpp -o stencil2d-cuda

stencil2d-cuda-double:
	$(CU) $(CUFLAGS) stencil2d-double.cu utils-double.cpp -o stencil2d-cuda-double

stencil2d-cuda-thread-halo:
	$(CU) $(CUFLAGS) stencil2d-thread-halo.cu utils.cpp -o stencil2d-cuda-thread-halo

stencil2d-cuda-reduce-arrays:
	$(CU) $(CUFLAGS) stencil2d-reduce-arrays.cu utils.cpp -o stencil2d-cuda-reduce-arrays

stencil2d-cuda-merge-kernels:
	$(CU) $(CUFLAGS) stencil2d-merge-kernels.cu utils.cpp -o stencil2d-cuda-merge-kernels

stencil2d-cuda-basic:
	$(CU) $(CUFLAGS) stencil2d-basic.cu utils.cpp -o stencil2d-cuda-basic

stencil2d-openacc:
	$(FC) $(FFLAGS) -acc -Mbackslash m_utils.F90 stencil2d_openacc.F90 -o stencil2d-openacc

clean:
	$(RM) -rf *~ *.o *.mod       \
	stencil2d-openacc            \
        stencil2d-cuda               \
        stencil2d-cuda-double        \
        stencil2d-cuda-thread-halo   \
        stencil2d-cuda-reduce-arrays \
        stencil2d-cuda-merge-kernels \
        stencil2d-cuda-basic
