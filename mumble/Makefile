include $(TOPDIR)/rules.mk

PKG_NAME:=mumble
PKG_VERSION:=1.5.634
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/mumble-voip/mumble/releases/download/v$(PKG_VERSION)
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=LICENSE

CMAKE_BINARY_SUBDIR := build

PKG_BUILD_DEPENDS:=boost qt5-tools mesa nlohmann-json gsl protobuf/host python3/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mumble
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Mumble - Open Source voice-chat software
	URL:=https://github.com/mumble-voip/mumble
	DEPENDS:=+alsa-lib +celt +libsndfile +libopenssl +libcap +libx11 +libxi +qt5-Concurrent +qt5-Core +qt5-DBus +qt5-Gui +qt5-Network +qt5-PrintSupport +qt5-Sql +qt5-Test +qt5-Widgets +qt5-Xml +qt5-svg +poco-all +protobuf +librnnoise +libspeex +libspeexdsp +libopus
endef

define Package/mumble/description
  Mumble is an open-source, low-latency, high quality voice chat software.
endef

define Build/Prepare
	$(call Build/Prepare/Default)
	$(RM) $(STAGING_DIR)/usr/bin/protoc*
	$(CP) $(STAGING_DIR_HOSTPKG)/bin/protoc* $(STAGING_DIR)/usr/bin/
endef

CMAKE_OPTIONS += \
	-Wno-dev \
	-DBUILD_SHARED_LIBS=ON \
	-Doverlay-xcompile=OFF \
	-Dspeechd=OFF \
	-Dice=OFF \
	-Drnnoise=ON \
	-Dbundled-celt=OFF \
	-Dbundle-qt-translations=OFF \
	-Dbundled-gsl=OFF \
	-Dbundled-json=OFF \
	-Dbundled-renamenoise=ON \
	-Dbundled-speex=OFF \
	-Dbundled-opus=OFF \
	-Dbundled-rnnoise=OFF \
	-Dupdate=OFF \
	-Dwarnings-as-errors=OFF \
	-Dzeroconf=OFF \
	-DBUILD_NUMBER="634"

define Package/mumble/install
	$(INSTALL_DIR) \
	  $(1)/usr/bin \
	  $(1)/usr/lib \
	  $(1)/usr/share

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
