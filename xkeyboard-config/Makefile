include $(TOPDIR)/rules.mk

PKG_NAME:=xkeyboard-config
PKG_VERSION:=2.41
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/data/xkeyboard-config
PKG_HASH:=f02cd6b957295e0d50236a3db15825256c92f67ef1f73bf1c77a4b179edf728f

PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=libxslt/host intltool/host gettext-full python3/host perl-xml-parser/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk

define Package/xkeyboard-config
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X keyboard configuration files
	URL:=http://xorg.freedesktop.org/
endef

define Package/xkeyboard-config/description
	This project provides a consistent, well-structured, frequently released,
	open source database of keyboard configuration data.
	The project is targeted at XKB-based systems.
endef

define Package/xkeyboard-config/install
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/X11 $(1)/usr/share/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/locale $(1)/usr/share/
endef

$(eval $(call BuildPackage,xkeyboard-config))
