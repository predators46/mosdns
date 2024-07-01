include $(TOPDIR)/rules.mk

PKG_NAME:=mumble
PKG_VERSION:=1.4.287
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/mumble-voip/mumble/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=LICENSE

CMAKE_BINARY_SUBDIR := build

PKG_BUILD_DEPENDS:=boost python3 qttools
PYTHON3_PKG_BUILD:=0

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/mumble
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Mumble - Open Source voice-chat software
	URL:=https://github.com/mumble-voip/mumble
	DEPENDS:=+alsa-lib +libavahi-compat-libdnssd +libsndfile +libopenssl +libcap +libx11 +libxi +qt5-Concurrent +qt5-Core +qt5-DBus +qt5-Gui +qt5-Network +qt5-PrintSupport +qt5-Sql +qt5-Test +qt5-Widgets +qt5-Xml +poco +protobuf +librnnoise +libspeex +libspeexdsp +libopus
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
	-DBUILD_NUMBER="${PKG_VERSION##*.}" \
	-DPython3_EXECUTABLE="$(STAGING_DIR_HOSTPKG)/bin/$(PYTHON3)"

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
