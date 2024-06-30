include $(TOPDIR)/rules.mk

PKG_NAME:=aprsdigi
PKG_VERSION:=3.11.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/n2ygk/aprsdigi/archive/v$(PKG_VERSION)
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=GPL-2.0 license
PKG_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/aprsdigi
	SECTION:=net
	CATEGORY:=Network
	TITLE:=a linux amateur radio APRS digipeater
	DEPENDS:=+libax25 +ax25tools
	URL:=https://github.com/n2ygk/aprsdigi
endef

define Package/aprsdigi/description
	Aprsdigi is a specialized Amateur Packet Radio (AX.25) UI-frame digipeater for the Automatic Position Reporting Systems, APRS(tm).
	It uses the Linux kernel AX.25 network stack as well as the SOCK_PACKET facility to listen for packets on one or more radio interfaces (ports) and repeat those packets -- with several possible modifications -- on the same or other interfaces.
	Aprsdigi can also use the Internet to tunnel connections among other APRS digipeaters and nodes using IPv4 or IPv6 UDP unicast or multicast.
endef

define Package/aprsdigi/conffiles
/etc/aprsdigi.conf
endef

CONFIGURE_ARGS += \
	--prefix=/usr \
	--sysconfdir=/etc \
	--without-mandoc \
	--disable-mandoc

define Package/aprsdigi/install
	$(INSTALL_DIR) \
	  $(1)/etc \
	  $(1)/usr/sbin

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/doc/aprsdigi/examples/aprsdigi.conf \
	  $(1)/etc/aprsdigi.conf
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/sbin/{aprsdigi,aprsmon} \
	  $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,aprsdigi))
