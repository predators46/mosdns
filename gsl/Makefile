include $(TOPDIR)/rules.mk

PKG_NAME:=gsl
PKG_VERSION:=3.1.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/microsoft/GSL.git
PKG_SOURCE_VERSION:=0f6dbc9e2915ef5c16830f3fa3565738de2a9230
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=License
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/GSL-$(PKG_VERSION)
CMAKE_BINARY_SUBDIR := build

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/gsl
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Guidelines Support Library
	URL:=https://github.com/microsoft/GSL
endef

define Package/gsl/description
	The Guidelines Support Library (GSL) contains functions and types that are suggested for use by the C++ Core Guidelines maintained by the Standard C++ Foundation.
endef

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/share

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/gsl \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share/cmake \
	  $(1)/usr/share/
endef

$(eval $(call BuildPackage,gsl))
