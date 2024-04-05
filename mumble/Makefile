include $(TOPDIR)/rules.mk

PKG_NAME:=mumble
PKG_VERSION:=1.4.287
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/mumble-voip/mumble/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=0b0f5fba6b6b1138311b661e81616c8f7283c048d456aa8248a17eee69a4f96f

PKG_MAINTAINER:=
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mumble
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Mumble - Open Source voice-chat software
	URL:=https://github.com/mumble-voip/mumble
	DEPENDS:=+alsa-lib +libavahi-compat-libdnssd +libsndfile +libopenssl +poco +protobuf +librnnoise +libspeex +libspeexdsp +libopus
endef

define Package/mumble/description
  Mumble is an open-source, low-latency, high quality voice chat software.
endef

CMAKE_OPTIONS += \
	-DBUILD_SHARED_LIBS=ON \
	-DCMAKE_BUILD_TYPE=MinSizeRel \
	-Doverlay-xcompile=OFF \
	-Dspeechd=OFF \
	-Dice=OFF \
	-Drnnoise=ON \
	-Dbundled-celt=ON \
	-Dbundle-qt-translations=ON \
	-Dbundled-speex=OFF \
	-Dbundled-opus=OFF \
	-Dbundled-rnnoise=OFF \
	-Dupdate=OFF

define Package/mumble/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tun2socks/badvpn-tun2socks $(1)/usr/bin/badvpn-tun2socks
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/udpgw/badvpn-udpgw $(1)/usr/bin/badvpn-udpgw
endef

$(eval $(call BuildPackage,mumble))
