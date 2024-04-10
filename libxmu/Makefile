include $(TOPDIR)/rules.mk

PKG_NAME:=libxmu
PKG_VERSION:=1.2.0
PKG_RELEASE:=1

PKG_SOURCE:=libXmu-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=072026fe305889538e5b0c5f9cbcd623d2c27d2b85dcd37ca369ab21590b6963

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libXmu-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD Zero Clause License
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros util-linux

include $(INCLUDE_DIR)/package.mk

define Package/libxmu
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X11 miscellaneous micro-utility library
	DEPENDS:=+libx11 +libxext +libxt
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxmu/description
	libXmu - X miscellaneous utility routines library
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libxmu/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxmu))
