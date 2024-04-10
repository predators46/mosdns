include $(TOPDIR)/rules.mk

PKG_NAME:=libice
PKG_VERSION:=1.1.1
PKG_RELEASE:=1

PKG_SOURCE:=libICE-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=03e77afaf72942c7ac02ccebb19034e6e20f456dcf8dddadfeb572aa5ad3e451

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libICE-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros xorgproto xtrans

include $(INCLUDE_DIR)/package.mk

define Package/libice
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X11 Inter-Client Exchange library
	URL:=http://xorg.freedesktop.org/
endef

define Package/libice/description
	libICE - Inter-Client Exchange Library
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libice/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libice))
