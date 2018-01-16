.PHONY : build clean

.DEFAULT_GOAL := build

SANDBOXING_NACL_DIR=$(shell realpath ../../Sandboxing_NaCl)
NACL_CLANG32=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/i686-nacl-clang
NACL_CLANG64=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/x86_64-nacl-clang
NACL_AR32=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/i686-nacl-ar
NACL_AR64=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/x86_64-nacl-ar

x32/non_nacl_build:
	-mkdir -p ./x32/non_nacl_build
	cd ./x32/non_nacl_build && CC=clang CFLAGS='-O3 -m32 -fPIC' LDFLAGS='-m32 -fPIC' ../../../configure
	$(MAKE) -C ./x32/non_nacl_build

x64/non_nacl_build:
	-mkdir -p ./x64/non_nacl_build
	cd ./x64/non_nacl_build && CC=clang CFLAGS='-O3 -fPIC' LDFLAGS='-fPIC' ../../../configure
	$(MAKE) -C ./x64/non_nacl_build

x32/nacl_build:
	-mkdir -p ./x32/nacl_build
	cd ./x32/nacl_build && CC=$(NACL_CLANG32) AR=$(NACL_AR32) CFLAGS='-O3 -m32 -fPIC' LDFLAGS='-m32 -fPIC' ../../../configure
	$(MAKE) -C ./x32/nacl_build

x64/nacl_build:
	-mkdir -p ./x64/nacl_build
	cd ./x64/nacl_build && CC=$(NACL_CLANG64) AR=$(NACL_AR64) CFLAGS='-O3 -fPIC' LDFLAGS='-fPIC' ../../../configure
	$(MAKE) -C ./x64/nacl_build

build: x32/non_nacl_build x64/non_nacl_build x32/nacl_build x64/nacl_build

clean:
	-rm -rf ./x32
	-rm -rf ./x64
