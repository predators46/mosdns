#
# Copyright (C) 2005-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qt5base
PKG_BASE_VERSION:=5.15
PKG_SUBVERSION:=0
PKG_VERSION:=$(PKG_BASE_VERSION).$(PKG_SUBVERSION)
PKG_RELEASE:=1

PKG_SOURCE:=qtbase-everywhere-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/$(PKG_BASE_VERSION)/$(PKG_VERSION)/submodules
PKG_HASH:=bc9a21e9f6fff9629019fdf9f989f064751d5073c3a28dc596def92f4d4275c6

HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/qtbase-everywhere-src-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/qtbase-everywhere-src-$(PKG_VERSION)

PKG_MAINTAINER:=
PKG_LICENSE:=LGPL-2.1
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk

define Package/qt5base
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Qt5 - QtBase components
  URL:=https://www.qt.io/
endef

define Package/qt5base/description
 This is a library for Abstract Syntax Notation One (ASN.1) and
 Distinguish Encoding Rules (DER) manipulation.
endef

HOST_CONFIGURE_ARGS += \
	--prefix=$(STAGING_DIR_HOST) \
	--hostprefix=$(STAGING_DIR_HOST) \
	--hostdatadir=$(STAGING_DIR_HOST)/share \
	--datadir=$(STAGING_DIR_HOST)/share \
	--archdatadir=$(STAGING_DIR_HOST)/lib \
	--gcc-sysroot=no \
	--verbose=yes \
	--opensource \
	--confirm-license \
	--release=yes \
	--optimized-tools=no \
	--optimize-size=no \
	--strip=no \
	--shared=yes \
	--framework=no \
	--reduce-exports=no \
	--reduce-relocations=no \
	--pch=no \
	--ltcg=no \
	--use-gold-linker=no \
	--warnings-are-errors=no \
	--pkg-config=yes \
	--compile-examples=no \
	--make=libs \
	--nomake=tools \
	--nomake=examples \
	--gui=yes \
	--widgets=no \
	--dbus=no \
	--accessibility=no \
	--doubleconversion=qt \
	--glib=no \
	--eventfd=no \
	--inotify=no \
	--iconv=no \
	--icu=no \
	--pcre=qt \
	--zlib=qt \
	--journald=no \
	--syslog=no \
	--ssl=no \
	--libproxy=no \
	--system-proxies=no \
	--cups=no \
	--fontconfig=no \
	--freetype=qt \
	--harfbuzz=no \
	--gtk=no \
	--opengl=no \
	--opengles3=no \
	--egl=no \
	--xcb-xlib=no \
	--directfb=no \
	--eglfs=no \
	--gbm=no \
	--linuxfb=no \
	--xcb=no \
	--libudev=no \
	--evdev=no \
	--libinput=no \
	--mtdev=no \
	--tslib=no \
	--bundled-xcb-xinput=no \
	--xkbcommon=yes \
	--gif=no \
	--ico=no \
	--libjpeg=no \
	--libpng=no \
	--sql-db2=no \
	--sql-ibase=no \
	--sql-mysql=no \
	--sql-oci=no \
	--sql-odbc=no \
	--sql-psql=no \
	--sql-sqlite=no \
	--sql-sqlite2=no \
	--sql-tds=no \
	--sqlite=no

CONFIGURE_ARGS += \
	--disable-doc \
	--disable-gcc-warnings \
	--disable-ld-version-script \
	--disable-valgrind-tests

define Build/InstallDev
	# $(INSTALL_DIR) $(1)/usr/bin
	# $(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libtasn1.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtasn1.{a,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libtasn1*.pc $(1)/usr/lib/pkgconfig/
endef

define Package/qt5base/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtasn1.so.* $(1)/usr/lib/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,qt5base))
