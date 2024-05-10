# 
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=llvm-project
PKG_VERSION:=18.1.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).src.tar.xz
PKG_SOURCE_URL:=https://github.com/llvm/llvm-project/releases/download/llvmorg-$(PKG_VERSION)
PKG_HASH:=skip

HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/$(PKG_NAME)-$(PKG_VERSION).src
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION).src

CMAKE_BINARY_SUBDIR := build
CMAKE_SOURCE_SUBDIR := llvm

CMAKE_INSTALL:=1

HOST_BUILD_DEPENDS:=libffi/host
PKG_BUILD_DEPENDS:=llvm/host

HOST_BUILD_PARALLEL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/llvm
  SECTION:=devel
  CATEGORY:=Development
  DEPENDS:=+libllvm +libstdcpp
  TITLE:=low level virtual machine compiler system
  URL:=http://llvm.org/
endef

define Package/libllvm
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libffi +libstdcpp
  TITLE:=low level virtual machine shared library
  URL:=http://llvm.org/
endef

TARGET_CFLAGS+=$(TARGET_CPPFLAGS)

CMAKE_HOST_OPTIONS += \
	-DCMAKE_BUILD_TYPE=Release \
	\
	-DLLVM_TARGETS_TO_BUILD="X86" \
	\
	-DLLVM_APPEND_VC_REV=OFF \
	-DLLVM_BUILD_DOCS=OFF \
	-DLLVM_BUILD_EXAMPLES=OFF \
	-DLLVM_BUILD_EXTERNAL_COMPILER_RT=ON \
	-DLLVM_BUILD_LLVM_DYLIB=ON \
	-DLLVM_BUILD_TESTS=OFF \
	-DLLVM_ENABLE_ASSERTIONS=OFF \
	-DLLVM_ENABLE_DUMP=ON \
	-DLLVM_ENABLE_EH=ON \
	-DLLVM_ENABLE_FFI=ON \
	-DLLVM_ENABLE_LIBCXX=OFF \
	-DLLVM_ENABLE_LIBEDIT=OFF \
	-DLLVM_ENABLE_PIC=ON \
	-DLLVM_ENABLE_RTTI=ON \
	-DLLVM_ENABLE_SPHINX=OFF \
	-DLLVM_ENABLE_TERMINFO=OFF \
	-DLLVM_ENABLE_LIBXML2=OFF \
	-DLLVM_ENABLE_ZLIB=OFF \
	-DLLVM_ENABLE_ZSTD=OFF \
	-DLLVM_INCLUDE_BENCHMARKS=OFF \
	-DLLVM_INCLUDE_EXAMPLES=OFF \
	-DLLVM_INSTALL_GTEST=OFF \
	-DLLVM_INSTALL_UTILS=ON \
	-DLLVM_LINK_LLVM_DYLIB=ON \
	-DLLVM_USE_PERF=ON

CMAKE_OPTIONS += \
	-DCMAKE_BUILD_TYPE=Release \
	-DCMAKE_SYSTEM_NAME="Linux" \
	\
	-DLLVM_TARGET_ARCH="AArch64" \
	-DLLVM_TARGETS_TO_BUILD="AArch64" \
	-DLLVM_DEFAULT_TARGET_TRIPLE="aarch64-openwrt-linux-musl" \
	-DLLVM_HOST_TRIPLE="aarch64-openwrt-linux-musl" \
	-DLLVM_NATIVE_TOOL_DIR="$(STAGING_DIR_HOSTPKG)/bin" \
	\
	-DLLVM_APPEND_VC_REV=OFF \
	-DLLVM_BUILD_DOCS=OFF \
	-DLLVM_BUILD_EXAMPLES=OFF \
	-DLLVM_BUILD_EXTERNAL_COMPILER_RT=ON \
	-DLLVM_BUILD_LLVM_DYLIB=ON \
	-DLLVM_BUILD_TESTS=OFF \
	-DLLVM_ENABLE_ASSERTIONS=OFF \
	-DLLVM_ENABLE_DUMP=ON \
	-DLLVM_ENABLE_EH=ON \
	-DLLVM_ENABLE_FFI=ON \
	-DLLVM_ENABLE_LIBCXX=OFF \
	-DLLVM_ENABLE_LIBEDIT=OFF \
	-DLLVM_ENABLE_PIC=ON \
	-DLLVM_ENABLE_RTTI=ON \
	-DLLVM_ENABLE_SPHINX=OFF \
	-DLLVM_ENABLE_TERMINFO=OFF \
	-DLLVM_ENABLE_LIBXML2=OFF \
	-DLLVM_ENABLE_ZLIB=OFF \
	-DLLVM_ENABLE_ZSTD=OFF \
	-DLLVM_INCLUDE_BENCHMARKS=OFF \
	-DLLVM_INCLUDE_EXAMPLES=OFF \
	-DLLVM_INSTALL_GTEST=OFF \
	-DLLVM_INSTALL_UTILS=ON \
	-DLLVM_LINK_LLVM_DYLIB=ON \
	-DLLVM_USE_PERF=ON

define Package/llvm/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin \
	$(1)/usr/
endef

define Package/libllvm/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib \
	$(1)/usr/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,libllvm))
$(eval $(call BuildPackage,llvm))
