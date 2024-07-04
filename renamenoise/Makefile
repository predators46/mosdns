include $(TOPDIR)/rules.mk

PKG_NAME:=renamenoise
PKG_VERSION:=0.2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/mumble-voip/ReNameNoise.git
PKG_SOURCE_VERSION:=2a551ab1261a1d5a5123c34eb6f4d108367d5cb4
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause license
PKG_LICENSE_FILES:=COPYING

#CMAKE_BINARY_SUBDIR := build

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/librenamenoise
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=RNNoise - is a noise suppression library based on a recurrent neural network.
	URL:=https://github.com/mumble-voip/ReNameNoise
endef

define Package/librenamenoise/description
	A fork of RNNoise with non-clashing symbols, the original tried and tested model, CMake support, and other optimizations
endef

CMAKE_OPTIONS += \
	-DBUILD_SHARED_LIBS=ON \
	-DRENAMENOISE_DEMO_EXECUTABLE=OFF

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include $(1)/usr/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librenamenoise.so.* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/renamenoise.pc $(1)/usr/lib/pkgconfig/
endef

define Package/librenamenoise/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librenamenoise.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,librenamenoise))
