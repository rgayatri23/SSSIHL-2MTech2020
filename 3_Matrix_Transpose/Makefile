CXX_gcc=gcc
CXX=nvcc
CXXFLAGS = -O3
LINK = ${CXX}
LINKFLAGS =

EXE = "MatTrans"

SRC_CU = Transpose.cu
SRC_CPP = timer.c

default: build
	echo "Start Build"

OBJ_CU = $(SRC_CU:.cu=.o)
OBJ_CPP = $(SRC_CPP:.c=.o)

CXXFLAGS += -I$(CUDA_ROOT)/include
CXXFLAGS += -I$(CUDA_ROOT)/samples/common/inc

build: $(EXE)

$(EXE): $(OBJ_CU) $(OBJ_CPP)
	$(LINK) $(LINKFLAGS) $(OBJ_CU) $(OBJ_CPUU) -o $(EXE).ex

$(OBJ_CU): $(SRC_CU)
		$(CXX) $(CXXFLAGS) -gencode arch=compute_70,code=sm_70 -c $< -o $@

$(OBJ_CPP): $(SRC_CPP)
		$(CXX) $(CXXFLAGS) -c $< -o $@

clean:
	rm -f *.ex *.o

# Compilation rules

%.o:%.cu
	$(CXX) $(CXXFLAGS) -c $<
