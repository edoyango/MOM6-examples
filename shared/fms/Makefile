# Configuration
BUILD ?= build
CODEBASE ?= ../../src/FMS2_gpu

TARGET = libFMS.a
MAKEFILE_IN = ../../src/MOM6/ac/deps/Makefile.fms.in
CONFIGURE_AC = ../../src/MOM6/ac/deps/configure.fms.ac
M4DIR = ../../src/MOM6/ac/deps/m4

# These are required by the FMS2 test suite
CPPFLAGS += -DAU_TEST_KIND_=r8_kind
CPPFLAGS += -DTEST_SVP_KIND_=8

# yaml support for modern diag_manager (fms_diag_*.F90)
# Set LIBYAML_ROOT=/path/to/libyaml to enable
ifdef LIBYAML_ROOT
CPPFLAGS        += -I$(LIBYAML_ROOT)/include
LDFLAGS         += -L$(LIBYAML_ROOT)/lib
LIBS            += -lyaml
CONFIGURE_FLAGS += --with-yaml
endif

include ../config/Libs.mk

$(BUILD)/$(TARGET): $(BUILD)/Makefile $(call find_src_files,$(CODEBASE))
	$(MAKE) -C $(BUILD) $(TARGET)
