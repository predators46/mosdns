include $(TOPDIR)/rules.mk

PKG_NAME:=xtrans
PKG_VERSION:=1.5.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib
PKG_HASH:=1ba4b703696bfddbf40bacf25bce4e3efb2a0088878f017a50e9884b0c8fb1bd

PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros libxslt/host

include $(INCLUDE_DIR)/package.mk

define Package/xtrans
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Libraries
	TITLE:=X transport library
	URL:=http://xorg.freedesktop.org/
endef

define Package/xtrans/description
	xtrans is a library of code that is shared among various X packages to handle
	network protocol transport in a modular fashion, allowing a single place to add new transport types.
	It is used by the X server, libX11, libICE, the X font server, and related components.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/X11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/aclocal $(1)/usr/share/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/pkgconfig $(1)/usr/share/
endef

$(eval $(call BuildPackage,xtrans))
