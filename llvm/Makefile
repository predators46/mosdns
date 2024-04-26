# 
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=llvm-project
PKG_VERSION:=17.0.6
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).src.tar.xz
PKG_SOURCE_URL:=https://github.com/llvm/llvm-project/releases/download/llvmorg-$(PKG_VERSION)
PKG_HASH:=skip

HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/$(PKG_NAME)-$(PKG_VERSION).src
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION).src

CMAKE_SOURCE_SUBDIR := llvm
CMAKE_INSTALL:=1

HOST_BUILD_DEPENDS:=ncurses/host libxml2/host zlib zstd llvm/host
PKG_BUILD_DEPENDS:=ncurses/host libxml2/host zlib zstd llvm/host
HOST_BUILD_PARALLEL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
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

#TARGET_CFLAGS+=$(TARGET_CPPFLAGS)

PKG_CMAKE_OPTS_COMMON = \
	-DCMAKE_CROSSCOMPILING=ON \
	-DCMAKE_BUILD_TYPE=Release \
	\
	-DLLVM_DEFAULT_TARGET_TRIPLE="$(GNU_TARGET_NAME)" \
	-DLLVM_HOST_TRIPLE="$(GNU_HOST_NAME)" \
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
	-DLLVM_ENABLE_TERMINFO=ON \
	-DLLVM_ENABLE_ZLIB=ON \
	-DLLVM_ENABLE_ZSTD=ON \
	-DLLVM_INCLUDE_BENCHMARKS=OFF \
	-DLLVM_INCLUDE_EXAMPLES=OFF \
	-DLLVM_INSTALL_GTEST=ON \
	-DLLVM_INSTALL_UTILS=ON \
	-DLLVM_LINK_LLVM_DYLIB=ON \
	-DLLVM_USE_PERF=ON

CMAKE_OPTIONS += \
	$(PKG_CMAKE_OPTS_COMMON) \
	-DLLVM_BUILD_TOOLS=ON \
	-DLLVM_TABLEGEN=$(STAGING_DIR_HOSTPKG)/usr/lib/llvm/bin/llvm-tblgen

CMAKE_HOST_OPTIONS += \
	$(PKG_CMAKE_OPTS_COMMON) \
	-DLLVM_BUILD_TOOLS=OFF \
	-DCMAKE_INSTALL_PREFIX="$(STAGING_DIR_HOSTPKG)/usr/lib/llvm" \
	-DCMAKE_BUILD_WITH_INSTALL_RPATH=TRUE \
	-DCMAKE_FIND_ROOT_PATH_MODE_INCLUDE=BOTH \
	-DCMAKE_FIND_ROOT_PATH_MODE_LIBRARY=BOTH \
	-DCMAKE_INSTALL_RPATH="$(STAGING_DIR_HOSTPKG)/usr/lib/llvm" \
	-DCMAKE_SKIP_RPATH=FALSE

#define Host/Install
#	$(call Host/Install/Default)
#	$(INSTALL_DIR) $(STAGING_DIR_HOSTPKG)/bin
#	$(INSTALL_BIN) $(HOST_BUILD_DIR)/bin/llvm-config $(STAGING_DIR_HOSTPKG)/bin/
#	$(INSTALL_BIN) $(HOST_BUILD_DIR)/bin/llvm-tblgen $(STAGING_DIR_HOSTPKG)/bin/
#endef

define Package/llvm/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin \
	$(1)/usr/
endef

define Package/libllvm/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libLLVM*.so* \
	$(1)/usr/lib
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,libllvm))
$(eval $(call BuildPackage,llvm))
