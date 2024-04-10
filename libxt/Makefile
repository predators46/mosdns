include $(TOPDIR)/rules.mk

PKG_NAME:=libxt
PKG_VERSION:=1.3.0
PKG_RELEASE:=1

PKG_SOURCE:=libXt-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=52820b3cdb827d08dc90bdfd1b0022a3ad8919b57a39808b12591973b331bf91

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/libXt-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros xorgproto

include $(INCLUDE_DIR)/package.mk

define Package/libxt
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X11 toolkit intrinsics library
	DEPENDS:=+libice +libsm +libx11
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxt/description
	libXt - X Toolkit Intrinsics library
endef

CONFIGURE_ARGS += \
	--enable-malloc0returnsnull

CONFIGURE_VARS += \
	PERL=$(STAGING_DIR_HOSTPKG)/usr/bin/perl

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/util \
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
endef

define Package/libxt/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxt))
