
# ======================================================
HFILES  += utest.hpp

CFILES  += utest.cpp


# Everything below this line is standard Makefile logic:
# ======================================================
DEPS    += $(HFILES)
OBJECTS += $(patsubst %.c,%.o,$(CFILES))    

# declare non-files
.PHONY: all 


# Use color enabled GCC output for readability
# ======================================================
 CC       = g++ # C   compiler
 CXX      = g++      # C++ Compiler


# ======================================================
 CXXFLAGS += -c
 CXXFLAGS += -g #produce debugging information
 CXXFLAGS += -fverbose-asm
#CXXFLAGS += -w # hide all warnings 
 CXXFLAGS += -save-temps
 CXXFLAGS += -Wall
 CXXFLAGS += -Wextra
#CXXFLAGS += -O3
 CXXFLAGS += -D__ADTS_DISPLAY


# ======================================================
 LPATHS += -L../adts/bin/x
 LNAMES += -ladts


 HPATHS += -I .
 HPATHS += -I ../adts/
# ======================================================


# ======================================================
# "all" should always be the first defined target to ensure default build
all: prepare \
     build   \
     cleanup


prepare:
	@echo ""
	@echo "Cleanup:"
	@echo "========"
	rm -fr bin *.[ii,s,o,so]

build:
	@echo ""
	@echo "Compile:"
	@echo "========"
	mkdir -p bin
	#$(CXX) $(HPATHS) $(CXXFLAGS) -o bin/utest.exe $(CFILES) $(LPATHS) $(LNAMES)
	$(CXX) $(HPATHS) $(CXXFLAGS) $(CFILES) -o bin/utest.exe $(LPATHS) $(LNAMES)

cleanup:
	@echo ""
	@echo "Unit Test:"
	@echo "=========="
	date
	mv *.[i,s,o] bin/
	ls -alF bin/
	bin/utest.exe 
