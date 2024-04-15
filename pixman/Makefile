include $(TOPDIR)/rules.mk

PKG_NAME:=pixman
PKG_VERSION:=0.43.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=48d8539f35488d694a2fef3ce17394d1153ed4e71c05d1e621904d574be5df19

PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=libpng

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk

define Package/pixman
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Xorg
	TITLE:=Image processing and manipulation library
	URL:=http://xorg.freedesktop.org/
endef

define Package/pixman/description
	Pixman is a library that provides low-level pixel manipulation
	features such as image compositing and trapezoid rasterization.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/pixman-1 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/pixman/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,pixman))
