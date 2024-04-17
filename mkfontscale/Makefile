include $(TOPDIR)/rules.mk

PKG_NAME:=mkfontscale
PKG_VERSION:=1.2.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/app
PKG_HASH:=2921cdc344f1acee04bcd6ea1e29565c1308263006e134a9ee38cf9c9d6fe75e

PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

HOST_BUILD_DEPENDS:=util-macros/host xorgproto/host libfontenc/host
PKG_BUILD_DEPENDS:=util-macros xorgproto

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/mkfontscale
	SECTION:=apps
	CATEGORY:=Applications
	SUBMENU:=Xorg
	TITLE:=Create an index of scalable font files for X
	DEPENDS:=+libfreetype +libfontenc +zlib
	URL:=http://xorg.freedesktop.org/
endef

define Package/mkfontscale/description
	mkfontscale creates the fonts.scale and fonts.dir index files used by the legacy X11 font system.
	It now includes the mkfontdir script previously distributed separately for compatibility with older X11 versions.
endef

HOST_CONFIGURE_VARS += \
	PKG_CONFIG_PATH= \
	$(STAGING_DIR_HOSTPKG)/lib/pkgconfig \
	$(STAGING_DIR_HOSTPKG)/share/pkgconfig

define Package/mkfontscale/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mkfontdir $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mkfontscale $(1)/usr/bin/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,mkfontscale))
