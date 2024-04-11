include $(TOPDIR)/rules.mk

PKG_NAME:=libxrender
PKG_VERSION:=0.9.11
PKG_RELEASE:=1

PKG_SOURCE:=libXrender-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=bc53759a3a83d1ff702fb59641b3d2f7c56e05051fa0cfa93501166fa782dc24

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libXrender-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros xorgproto

include $(INCLUDE_DIR)/package.mk

define Package/libxrender
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X Rendering Extension client library
	DEPENDS:=+libx11
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxrender/description
	libXrender - library for the Render Extension to the X11 protocol
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libxrender/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxrender))
