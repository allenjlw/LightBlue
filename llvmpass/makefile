
.PHONE=all clean

# The name of the plugin.
SRC = $(wildcard *.cpp)
OBJ = $(SRC:.cpp=.o)
LIB_OUT = BTanalysis

# LLVM paths. Note: you probably need to update these.
LLVM_DIR_INC1 = /usr/include/llvm-14/
LLVM_DIR_INC2 = /usr/include/llvm-c-14/

# Compiler flags.
CXXFLAGS  = -I$(LLVM_DIR_INC1) -I$(LLVM_DIR_INC2) -I.
CXXFLAGS += -D__STDC_LIMIT_MACROS -D__STDC_CONSTANT_MACROS -Wno-long-long
CXXFLAGS += -fPIC -fvisibility-inlines-hidden
CXXFLAGS += -fno-exceptions -fno-rtti -std=c++14
CXXFLAGS += -Wall -g

# Linker flags.
LDFLAGS = -shared -Wl,-undefined,dynamic_lookup

all : $(LIB_OUT).so

$(LIB_OUT).so : $(OBJ)
	@clang++ $(LDFLAGS) -o $(LIB_OUT).so $(OBJ)

%.o : %.cpp
	@clang++ $(CXXFLAGS) -c -o $@ $<

clean :
	@rm -fv $(LIB_OUT).so $(OBJ)
