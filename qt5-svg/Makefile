#
# Copyright (C) 2019 Openwrt.org
#
# This is free software, licensed under the Apache License, Version 2.0 .
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qt5-svg
PKG_BASE:=5.15
PKG_BUGFIX:=14
PKG_VERSION:=$(PKG_BASE).$(PKG_BUGFIX)
PKG_RELEASE:=1

PKG_SOURCE:=qtsvg-everywhere-opensource-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:= \
		http://master.qt.io/archive/qt/$(PKG_BASE)/$(PKG_VERSION)/submodules \
		http://mirrors.tuna.tsinghua.edu.cn/qt/archive/qt/$(PKG_BASE)/$(PKG_VERSION)/submodules \
		http://qt.mirror.constant.com/archive/qt/$(PKG_BASE)/$(PKG_VERSION)/submodules
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/qtsvg-everywhere-src-$(PKG_VERSION)

PKG_BUILD_PARALLEL:=1
#PKG_BUILD_DEPENDS:=qtbase

include $(INCLUDE_DIR)/package.mk

define Package/qt5-svg
  SECTION:=libs
  CATEGORY:=Libraries
  SUBMENU:=Qt5
  TITLE:=qtsvg
  URL:=http://qt-project.org
  DEPENDS:=+qt5-Core
endef

define Build/Configure
	cd $(PKG_BUILD_DIR) && qmake -o Makefile qtsvg.pro
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR)
endef

define Build/InstallDev
	$(MAKE) -C $(PKG_BUILD_DIR) install
endef

define Package/qt5-svg/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/lib/libQt5Svg.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,qt5-svg))
