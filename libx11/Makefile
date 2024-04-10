include $(TOPDIR)/rules.mk

PKG_NAME:=libx11
PKG_VERSION:=1.8.9
PKG_RELEASE:=1

PKG_SOURCE:=libX11-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=779d8f111d144ef93e2daa5f23a762ce9555affc99592844e71c4243d3bd3262

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libX11-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD 1-Clause License
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=xtrans xorgproto util-macros perl/host

include $(INCLUDE_DIR)/package.mk

define Package/libx11
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X11 client-side library
	DEPENDS:=+libxcb
	URL:=http://xorg.freedesktop.org/
endef

define Package/libx11/description
	libX11 - Core X11 protocol client library
endef

CONFIGURE_ARGS += \
	--enable-malloc0returnsnull

CONFIGURE_VARS += \
	PERL=$(STAGING_DIR_HOSTPKG)/usr/bin/perl

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/src/util \
	CC="$(HOSTCC)" \
	CFLAGS="$(HOST_CFLAGS)" \
	CPPFLAGS="$(HOST_CPPFLAGS)" \
	LDFLAGS="$(HOST_LDFLAGS)"
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/X11 $(1)/usr/share/
endef

define Package/libx11/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libx11))
