include $(TOPDIR)/rules.mk

PKG_NAME:=util-macros
PKG_VERSION:=1.20.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/util
PKG_HASH:=0b86b262dbe971edb4ff233bc370dfad9f241d09f078a3f6d5b7f4b8ea4430db

PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/$(PKG_NAME)-$(PKG_VERSION)
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk

define Package/util-macros
  SECTION:=xorg
  CATEGORY:=Xorg
  SUBMENU:=Utilities
  TITLE:=X.Org Autotools macros
  URL:=http://xorg.freedesktop.org/
endef

define Package/util-macros/description
  GNU autoconf macros shared across X.Org projects
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/aclocal $(1)/usr/share/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/pkgconfig $(1)/usr/share/
endef

$(eval $(call BuildPackage,util-macros))
$(eval $(call HostBuild))
