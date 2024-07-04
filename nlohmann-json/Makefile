include $(TOPDIR)/rules.mk

PKG_NAME:=nlohmann-json
PKG_VERSION:=3.11.3
PKG_RELEASE:=1

PKG_SOURCE:=json-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/nlohmann/json/archive/v$(PKG_VERSION)
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT license
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/json-$(PKG_VERSION)
CMAKE_BINARY_SUBDIR := build

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/nlohmann-json
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=JSON for Modern C++
	URL:=https://github.com/nlohmann/json
endef

define Package/nlohmann-json/description
	JSON for Modern C++
endef

CMAKE_OPTIONS += \
	-DJSON_MultipleHeaders=ON

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/share

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/nlohmann \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/{cmake,pkgconfig} \
	  $(1)/usr/share/
endef

$(eval $(call BuildPackage,nlohmann-json))
