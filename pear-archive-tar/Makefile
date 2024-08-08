#
# Copyright (C) 2007-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pear-archive-tar
PKG_VERSION:=1.5.0
PKG_RELEASE:=1

PKG_SOURCE:=Archive_Tar-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://download.pear.php.net/package/
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/Archive_Tar-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/pear-archive-tar
  SUBMENU:=PHP
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=PEAR Archive-Tar
  URL:=http://pear.php.net/package/Archive_Tar
  DEPENDS:=+pear
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/pear-archive-tar/install
	$(INSTALL_DIR) $(1)/usr/lib/php
	$(CP) $(PKG_BUILD_DIR)/Archive $(1)/usr/lib/php/
endef

$(eval $(call BuildPackage,pear-archive-tar))
