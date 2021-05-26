#================================================
# *** Makefile for test/main.cpp ***
# Author:	Ryan Clement
# Date:		May 2021 
#
# Commands:
# Build and Link: 	make
# Run:				make run
# Clean:			make clean
#================================================

CXX := icpc
SRCDIR := src
BUILDDIR := release
CFLAGS := -O3 -qopenmp -std=c++17
OTHER_CFLAGS :=
LIBFLAGS := -qopenmp

TARGET := $(BUILDDIR)/hello_world.x

icpc: $(TARGET)

SOURCES := $(wildcard $(SRCDIR)/*.cpp)
OBJECTS := $(patsubst $(SRCDIR)/%,$(BUILDDIR)/%,$(SOURCES:.cpp=.o))

$(TARGET): $(OBJECTS)
	@echo " Linking..."
	$(CXX) $^ $(LIBFLAGS) -o $(TARGET)

$(BUILDDIR)/%.o: $(SRCDIR)/%.cpp
	@mkdir -p $(BUILDDIR)
	$(CXX) -c $(CFLAGS) $(EXTRA_CFLAGS) -o $@ $< 

run: $(TARGET)
ifeq ($(shell uname -s),Darwin)
	@export  DYLD_LIBRARY_PATH="$(LIBRARY_PATH)"; ./$(TARGET)
else
	./$(TARGET)
endif

clean:
	@echo " Cleaning..."
	@rm -fr $(BUILDDIR) $(TARGET) 2>/dev/null || true
	@rm -f *.png

.PHONY: clean