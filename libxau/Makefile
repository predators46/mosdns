include $(TOPDIR)/rules.mk

PKG_NAME:=libxau
PKG_VERSION:=1.0.11
PKG_RELEASE:=1

PKG_SOURCE:=libXau-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=f3fa3282f5570c3f6bd620244438dbfbdd580fc80f02f549587a0f8ab329bbeb

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libXau-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros xorgproto

include $(INCLUDE_DIR)/package.mk

define Package/libxau
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X11 authorisation library
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxau/description
  Functions for handling Xauthority files and entries.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libxau/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxau))
