include $(TOPDIR)/rules.mk

PKG_NAME:=ax25apps
PKG_VERSION:=1.2.2
PKG_RELEASE:=1

PKG_SOURCE:=libax25-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/ve7fet/linuxax25/archive/refs/tags/
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LGPL-2.1-or-later
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DIR:=$(BUILD_DIR)/linuxax25-libax25-$(PKG_VERSION)

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/ax25apps
	SECTION:=net
	CATEGORY:=Network
	TITLE:=programs for the amateur radio (hamradio) protocol AX.25
	DEPENDS:=+libncurses +libax25
	URL:=https://github.com/ve7fet/linuxax25
endef

define Package/ax25apps/description
	programs for the amateur radio (hamradio) protocol AX.25
endef

MAKE_PATH:=ax25apps
CONFIGURE_PATH:=ax25apps

CONFIGURE_ARGS += \
	--prefix=/usr \
	--sysconfdir=/etc

define Package/ax25apps/install
	$(INSTALL_DIR) \
	  $(1)/etc \
	  $(1)/usr/bin \
	  $(1)/usr/sbin

	$(CP) \
	  $(PKG_INSTALL_DIR)/etc/ax25 \
	  $(1)/etc/
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/* \
	  $(1)/usr/bin/
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/sbin/* \
	  $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ax25apps))
