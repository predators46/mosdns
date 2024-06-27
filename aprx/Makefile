include $(TOPDIR)/rules.mk

PKG_NAME:=aprx
PKG_VERSION:=2.9.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://thelifeofkenneth.com/aprx/release/
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause license
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/aprx
	SECTION:=net
	CATEGORY:=Network
	TITLE:=A highly configurable APRS I-gate/Digipeater Daemon
	DEPENDS:=+libstdcpp +libpthread +libax25 +ax25apps +ax25tools
	URL:=https://thelifeofkenneth.com/aprx/
endef

define Package/aprx/description
	Aprx is a software package designed to run on any POSIX platform (Linux/BSD/Unix/etc.) and act as an APRS Digipeater and/or Internet Gateway.
	Aprx is able to support most APRS infrastructure deployments, including single stand-alone digipeaters, receive-only Internet gateways, full RF-gateways for bi-directional routing of traffic, and multi-port digipeaters operating on multiple channels or with multiple directional transceivers.
endef

#TARGET_LDFLAGS+= -fstack-protector-strong

CONFIGURE_ARGS += \
	--prefix=/usr \
	--with-embedded \
	--without-pthread

define Package/aprx/install
	$(INSTALL_DIR) \
	  $(1)/usr/sbin

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/sbin/{aprx,aprx-stat} \
	  $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,aprx))
