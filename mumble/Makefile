include $(TOPDIR)/rules.mk

PKG_NAME:=mumble
PKG_VERSION:=1.5.634
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/mumble-voip/mumble/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=boost

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mumble
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Mumble - Open Source voice-chat software
	URL:=https://github.com/mumble-voip/mumble
	DEPENDS:=+alsa-lib +libavahi-compat-libdnssd +libsndfile +libopenssl +libcap +libx11 +libxi +poco +protobuf +librnnoise +libspeex +libspeexdsp +libopus
endef

define Package/mumble/description
  Mumble is an open-source, low-latency, high quality voice chat software.
endef

define Package/mumble/conffiles
/etc/murmur.ini
endef

CMAKE_OPTIONS += \
	-DBUILD_SHARED_LIBS=ON \
	-DCMAKE_BUILD_TYPE=MinSizeRel \
	-Doverlay-xcompile=OFF \
	-Dspeechd=OFF \
	-Dice=OFF \
	-Drnnoise=ON \
	-Dtranslations=OFF \
	-Dbundled-celt=ON \
	-Dbundle-qt-translations=OFF \
	-Dbundled-speex=OFF \
	-Dbundled-opus=OFF \
	-Dbundled-rnnoise=OFF \
	-Dupdate=OFF \
	-DBUILD_NUMBER="1.5.634"

define Package/mumble/install
	$(INSTALL_DIR) \
	  $(1)/etc \
	  $(1)/usr/bin \
	  $(1)/usr/lib \
	  $(1)/usr/share

	$(CP) \
	  $(PKG_INSTALL_DIR)/etc/murmur.ini \
	  $(1)/etc/murmur.ini

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/* \
	  $(1)/usr/bin/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/mumble \
	  $(1)/usr/lib/
	
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/{applications,icons,metainfo} \
	  $(1)/usr/share/
endef

$(eval $(call BuildPackage,mumble))
