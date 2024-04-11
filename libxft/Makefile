include $(TOPDIR)/rules.mk

PKG_NAME:=libxft
PKG_VERSION:=2.3.8
PKG_RELEASE:=1

PKG_SOURCE:=libXft-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=5e8c3c4bc2d4c0a40aef6b4b38ed2fb74301640da29f6528154b5009b1c6dd49

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libXft-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros xorgproto

include $(INCLUDE_DIR)/package.mk

define Package/libxft
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=FreeType-based font drawing library for X
	DEPENDS:=+fontconfig +libfreetype +libx11 +libxrender
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxft/description
	libXft - X FreeType library
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libxft/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxft))
