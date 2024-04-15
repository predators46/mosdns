include $(TOPDIR)/rules.mk

PKG_NAME:=font-util
PKG_VERSION:=1.4.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/font
PKG_HASH:=5c9f64123c194b150fee89049991687386e6ff36ef2af7b80ba53efaf368cc95

PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD 2-Clause NetBSD License
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros

include $(INCLUDE_DIR)/package.mk

define Package/font-util
	SECTION:=font
	CATEGORY:=Font
	SUBMENU:=Xorg
	TITLE:=X.Org font utilities
	URL:=http://xorg.freedesktop.org/
endef

define Package/font-util/description
	X.Org font package creation/installation utilities
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/aclocal $(1)/usr/share/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/fonts $(1)/usr/share/
endef

define Package/font-util/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/bdftruncate $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/ucs2any $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/fonts $(1)/usr/share/
endef

$(eval $(call BuildPackage,font-util))
