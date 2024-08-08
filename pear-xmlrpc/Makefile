#
# Copyright (C) 2007-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pear-xmlrpc
PKG_VERSION:=1.5.5
PKG_RELEASE:=1

PKG_SOURCE:=XML_RPC-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://download.pear.php.net/package/
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/XML_RPC-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/pear-xmlrpc
  SUBMENU:=PHP
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=PEAR XML-RPC
  URL:=http://pear.php.net/package/XML_RPC
  DEPENDS:=+pear
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/pear-xmlrpc/install
	$(INSTALL_DIR) $(1)/usr/lib/php
	$(CP) $(PKG_BUILD_DIR)/XML $(1)/usr/lib/php/
endef

$(eval $(call BuildPackage,pear-xmlrpc))
