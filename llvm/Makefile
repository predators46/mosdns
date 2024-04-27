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

CMAKE_BINARY_SUBDIR := build
CMAKE_SOURCE_SUBDIR := llvm

CMAKE_INSTALL:=1

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

#TARGET_CFLAGS+=$(TARGET_CPPFLAGS)

CMAKE_HOST_OPTIONS += \
	-DCMAKE_BUILD_TYPE=Release \
	-DCMAKE_INSTALL_PREFIX="$(STAGING_DIR_HOSTPKG)/usr/lib/llvm/lib" \
	-DLLVM_TARGETS_TO_BUILD="ARM;AArch64;X86" \
	-DLLVM_ENABLE_PROJECTS="lld;clang;lldb;clang-tools-extra" \
	-DLLVM_ENABLE_TERMINFO=OFF \
	-DLLVM_ENABLE_LIBXML2=OFF \
	-DLLVM_ENABLE_ZLIB=OFF

CMAKE_OPTIONS += \
	-DCMAKE_BUILD_TYPE=Release \
	-DCMAKE_SYSTEM_NAME=Linux \
	-DLLVM_TARGETS_TO_BUILD="ARM;AArch64;X86" \
	-DLLVM_ENABLE_PROJECTS="lld;clang;lldb;clang-tools-extra" \
	-DLLVM_NATIVE_TOOL_DIR=/home/runner/work/mosdns/mosdns/sdk/build_dir/hostpkg/llvm-project-17.0.6.src/build/bin \
	-DCMAKE_FIND_ROOT_PATH_MODE_PROGRAM=NEVER \
	-DCMAKE_FIND_ROOT_PATH_MODE_INCLUDE=ONLY \
	-DCMAKE_FIND_ROOT_PATH_MODE_LIBRARY=ONLY \
	-DCMAKE_FIND_ROOT_PATH_MODE_PACKAGE=ONLY

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
