#
# Copyright (C) 2007-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pear-structures-graph
PKG_VERSION:=1.2.0
PKG_RELEASE:=1

PKG_SOURCE:=Structures_Graph-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://download.pear.php.net/package/
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/Structures_Graph-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/pear-structures-graph
  SUBMENU:=PHP
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=PEAR Structures-Graph
  URL:=http://pear.php.net/package/Structures_Graph
  DEPENDS:=+pear
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/pear-structures-graph/install
	$(INSTALL_DIR) $(1)/usr/lib/php
	$(CP) $(PKG_BUILD_DIR)/Structures $(1)/usr/lib/php/
endef

$(eval $(call BuildPackage,pear-structures-graph))
