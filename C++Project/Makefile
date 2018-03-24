# Common parameters
EXE := ${project_name}
BUILD_DIR := build
SRC_DIR := src
INC_DIR := include

# Compiler and linker
CC := g++
SRC_EXTENSION := cpp
OBJ_EXTENSION := o
COMPILER_FLAGS := 
LINKER_FLAGS :=

#
# Implementation
#

# Find objects thanks to sources
SRCS := $(wildcard $(SRC_DIR)/*.$(SRC_EXTENSION)) $(wildcard $(SRC_DIR)/**/*.$(SRC_EXTENSION))
OBJS := $(SRCS:$(SRC_DIR)/%.$(SRC_EXTENSION)=$(BUILD_DIR)/%.$(OBJ_EXTENSION))

# Include what needs to be included and compile without linking
CFLAGS := -I$(INC_DIR) -c

all: $(dir $(OBJS)) $(BUILD_DIR)/$(EXE)

# Create missing directories
%/:
	mkdir $@

# Link
$(BUILD_DIR)/$(EXE): $(OBJS)
	$(CC) $(LINKER_FLAGS) $(OBJS) -o $@

# Compile
$(BUILD_DIR)/%.$(OBJ_EXTENSION): $(SRC_DIR)/%.$(SRC_EXTENSION)
	$(CC) $(CFLAGS) $(COMPILER_FLAGS) $< -o $@
	$(CC) $(CFLAGS) $(COMPILER_FLAGS) $< -MM -MT$@ > $@.d

# Cleanup
clean:
	rm -rf $(BUILD_DIR)/*

# Include generated dependecies
-include $(wildcard $(BUILD_DIR)/*.d)
