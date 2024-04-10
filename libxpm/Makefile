include $(TOPDIR)/rules.mk

PKG_NAME:=libxpm
PKG_VERSION:=3.5.17
PKG_RELEASE:=1

PKG_SOURCE:=libXpm-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=64b31f81019e7d388c822b0b28af8d51c4622b83f1f0cb6fa3fc95e271226e43

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libXpm-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros util-linux

include $(INCLUDE_DIR)/package.mk

define Package/libxpm
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X11 pixmap library
	DEPENDS:=+libx11 +libxext +libxt
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxpm/description
	libXpm - X Pixmap (XPM) image file format library
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/cxpm $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/sxpm $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libxpm/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/cxpm $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/sxpm $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxpm))
