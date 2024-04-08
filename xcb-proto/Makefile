include $(TOPDIR)/rules.mk

PKG_NAME:=xcb-proto
PKG_VERSION:=1.16.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/proto
PKG_HASH:=a75a1848ad2a89a82d841a51be56ce988ff3c63a8d6bf4383ae3219d8d915119

PYTHON3_PKG_BUILD:=0
PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/xcb-proto
  SECTION:=xorg
  CATEGORY:=Xorg
  SUBMENU:=Protocol
  TITLE:=XML-XCB protocol descriptions
  URL:=http://xorg.freedesktop.org/
endef

define Package/xcb-proto/description
  XML-XCB protocol descriptions used by libxcb for the X11 protocol & extensions
endef

CONFIGURE_VARS += \
	PYTHON="$(STAGING_DIR_HOSTPKG)/bin/$(PYTHON3)" \
	PYTHON_CPPFLAGS="$(shell $(STAGING_DIR)/host/bin/$(PYTHON3)-config --includes)" \
	PYTHON_LIBS="$(shell $(STAGING_DIR)/host/bin/$(PYTHON3)-config --libs)"

define Build/InstallDev
	$(INSTALL_DIR) $(1)/$(PYTHON3_PKG_DIR)
	$(CP) $(PKG_INSTALL_DIR)/$(PYTHON3_PKG_DIR)/xcbgen $(1)/$(PYTHON3_PKG_DIR)
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/pkgconfig $(1)/usr/share/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/xcb $(1)/usr/share/
	$(SED) 's,/usr/share,$$$${prefix}/share,g' $(1)/usr/share/pkgconfig/xcb-proto.pc
endef

$(eval $(call BuildPackage,xcb-proto))
