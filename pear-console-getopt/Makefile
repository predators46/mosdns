#
# Copyright (C) 2007-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pear-console-getopt
PKG_VERSION:=1.4.3
PKG_RELEASE:=1

PKG_SOURCE:=Console_Getopt-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://download.pear.php.net/package/
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/Console_Getopt-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/pear-console-getopt
  SUBMENU:=PHP
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=PEAR Console-Getopt
  URL:=http://pear.php.net/package/Console_Getopt
  DEPENDS:=+pear
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/pear-console-getopt/install
	$(INSTALL_DIR) $(1)/usr/lib/php
	$(CP) $(PKG_BUILD_DIR)/Console $(1)/usr/lib/php/
endef

$(eval $(call BuildPackage,pear-console-getopt))
