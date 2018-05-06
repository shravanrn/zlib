.PHONY : build clean

.DEFAULT_GOAL := build

SANDBOXING_NACL_DIR=$(shell realpath ../../Sandboxing_NaCl)
NACL_CLANG32=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/i686-nacl-clang
NACL_CLANG64=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/x86_64-nacl-clang
NACL_AR32=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/i686-nacl-ar
NACL_AR64=$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/bin/x86_64-nacl-ar
NACL_CLANG++32=$(NACL_CLANG32)++
NACL_CLANG++64=$(NACL_CLANG64)++

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
	mkdir -p ./x32/nacl_build/mainCombine
	cd ./x32/nacl_build/mainCombine && $(NACL_AR32) -x ../libz.a
	cd ./x32/nacl_build/mainCombine && $(NACL_CLANG++32) -fPIC -m32 -B$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib/ -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_32-nacl/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib ./*.o -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib -L$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_32-nacl/lib -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib -ldyn_ldr_sandbox_init -o ./libz.nexe

x64/nacl_build:
	-mkdir -p ./x64/nacl_build
	cd ./x64/nacl_build && CC=$(NACL_CLANG64) AR=$(NACL_AR64) CFLAGS='-O3 -fPIC' LDFLAGS='-fPIC' ../../../configure
	$(MAKE) -C ./x64/nacl_build
	mkdir -p ./x64/nacl_build/mainCombine
	cd ./x64/nacl_build/mainCombine && $(NACL_AR64) -x ../libz.a
	cd ./x64/nacl_build/mainCombine && $(NACL_CLANG++64) -fPIC -m64 -B$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib/ -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_64-nacl/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib ./*.o -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib -L$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_64-nacl/lib -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib -ldyn_ldr_sandbox_init -o ./libz.nexe

x32/non_nacl_build_debug:
	-mkdir -p ./x32/non_nacl_build_debug
	cd ./x32/non_nacl_build_debug && CC=clang CFLAGS='-O3 -m32 -fPIC -g' LDFLAGS='-m32 -fPIC -g' ../../../configure
	$(MAKE) -C ./x32/non_nacl_build_debug

x64/non_nacl_build_debug:
	-mkdir -p ./x64/non_nacl_build_debug
	cd ./x64/non_nacl_build_debug && CC=clang CFLAGS='-O3 -fPIC -g' LDFLAGS='-fPIC -g' ../../../configure
	$(MAKE) -C ./x64/non_nacl_build_debug

x32/nacl_build_debug:
	-mkdir -p ./x32/nacl_build_debug
	cd ./x32/nacl_build_debug && CC=$(NACL_CLANG32) AR=$(NACL_AR32) CFLAGS='-O3 -m32 -fPIC -g' LDFLAGS='-m32 -fPIC -g' ../../../configure
	$(MAKE) -C ./x32/nacl_build_debug
	mkdir -p ./x32/nacl_build_debug/mainCombine
	cd ./x32/nacl_build_debug/mainCombine && $(NACL_AR32) -x ../libz.a
	cd ./x32/nacl_build_debug/mainCombine && $(NACL_CLANG++32) -fPIC -m32 -B$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib/ -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_32-nacl/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib ./*.o -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib -L$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_32-nacl/lib -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-32/lib -ldyn_ldr_sandbox_init -o ./libz.nexe

x64/nacl_build_debug:
	-mkdir -p ./x64/nacl_build_debug
	cd ./x64/nacl_build_debug && CC=$(NACL_CLANG64) AR=$(NACL_AR64) CFLAGS='-O3 -fPIC -g' LDFLAGS='-fPIC -g' ../../../configure
	$(MAKE) -C ./x64/nacl_build_debug
	mkdir -p ./x64/nacl_build_debug/mainCombine
	cd ./x64/nacl_build_debug/mainCombine && $(NACL_AR64) -x ../libz.a
	cd ./x64/nacl_build_debug/mainCombine && $(NACL_CLANG++64) -fPIC -m64 -B$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib/ -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_64-nacl/lib -Wl,-rpath-link,$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib ./*.o -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib -L$(SANDBOXING_NACL_DIR)/native_client/toolchain/linux_x86/pnacl_newlib/x86_64-nacl/lib -L$(SANDBOXING_NACL_DIR)/native_client/scons-out/nacl-x86-64/lib -ldyn_ldr_sandbox_init -o ./libz.nexe


build: x32/non_nacl_build x64/non_nacl_build x32/nacl_build x64/nacl_build x32/non_nacl_build_debug x64/non_nacl_build_debug x32/nacl_build_debug x64/nacl_build_debug

clean:
	-rm -rf ./x32
	-rm -rf ./x64
