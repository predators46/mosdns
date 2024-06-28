include $(TOPDIR)/rules.mk

PKG_NAME:=direwolf
PKG_VERSION:=1.7
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/wb2osz/direwolf/archive/$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=GPL-2.0 license
PKG_LICENSE_FILES:=LICENSE

CMAKE_BINARY_SUBDIR := build

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/direwolf
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Software soundcard AX.25 packet modem/TNC and APRS encoder/decoder
	DEPENDS:=+alsa-lib +libavahi-client +libudev-zero +libgps +hamlib
	URL:=https://github.com/wb2osz/direwolf
endef

define Package/direwolf/description
	Dire Wolf is a software "soundcard" AX.25 packet modem/TNC and APRS encoder/decoder.
	It can be used stand-alone to observe APRS traffic, as a tracker, digipeater, APRStt gateway, or Internet Gateway (IGate).
endef

define Package/direwolf/conffiles
/etc/direwolf/
endef

define Package/direwolf/install
	$(INSTALL_DIR) \
	  $(1)/etc/direwolf \
	  $(1)/usr/bin \
	  $(1)/usr/share \
	  $(1)/lib/udev/rules.d

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/doc/direwolf/conf/* \
	  $(1)/etc/direwolf/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/* \
	  $(1)/usr/bin/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/{applications,direwolf,pixmaps} \
	  $(1)/usr/share/
	
	$(CP) \
	  $(PKG_INSTALL_DIR)/etc/udev/rules.d/99-direwolf-cmedia.rules \
	  $(1)/lib/udev/rules.d/
endef

$(eval $(call BuildPackage,direwolf))
