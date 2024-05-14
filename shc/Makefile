include $(TOPDIR)/rules.mk

PKG_NAME:=shc
PKG_VERSION:=4.0.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/neurobin/shc/tar.gz/$(PKG_VERSION)?
PKG_HASH:=7d7fa6a9f5f53d607ab851d739ae3d3b99ca86e2cb1425a6cab9299f673aee16

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=GPL-3.0 license
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/shc
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Shell Script Compiler
	DEPENDS:=+libstdcpp
	URL:=https://github.com/neurobin/shc
endef

define Package/shc/description
	Shc takes a script,which is specified on the command line and produces C source code.
	The generated source code is then compiled and linked to produce a stripped binary executable.
endef

define Package/shc/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/shc $(1)/usr/bin/
endef

$(eval $(call BuildPackage,shc))
