include $(TOPDIR)/rules.mk

PKG_NAME:=shapelib
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://download.osgeo.org/shapelib/
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=License MIT
PKG_LICENSE_FILES:=LICENSE-LGPL LICENSE-MIT

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/shapelib
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Simple C API for reading and writing ESRI Shapefiles
	DEPENDS:=+libstdcpp
	URL:=http://shapelib.maptools.org/
endef

define Package/shapelib/description
	C library for reading, writing and updating ESRI Shapefiles, and the associated attribute file
endef

CONFIGURE_ARGS += \
	--prefix=/usr

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/shapefil.h \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{pkgconfig,*.so*,*.a} \
	  $(1)/usr/lib/
endef

define Package/shapelib/install
	$(INSTALL_DIR) \
	  $(1)/usr/bin \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/* \
	  $(1)/usr/bin/
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

$(eval $(call BuildPackage,shapelib))
