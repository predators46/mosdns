include $(TOPDIR)/rules.mk

PKG_NAME:=libxi
PKG_VERSION:=1.8.1
PKG_RELEASE:=1

PKG_SOURCE:=libXi-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=89bfc0e814f288f784202e6e5f9b362b788ccecdeb078670145eacd8749656a7

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libXi-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros xorgproto libxfixes

include $(INCLUDE_DIR)/package.mk

define Package/libxi
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X11 Input extension library
	DEPENDS:=+libx11 +libxext
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxi/description
	libXi - library for the X Input Extension
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libxi/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxi))
