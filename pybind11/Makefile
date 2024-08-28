include $(TOPDIR)/rules.mk

PKG_NAME:=pybind11
PKG_VERSION:=2.13.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/pybind/pybind11/archive/v$(PKG_VERSION)
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=License
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python-setuptools-scm/host
PKG_BUILD_DEPENDS:=python-setuptools-scm/host

CMAKE_BINARY_SUBDIR := build

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(INCLUDE_DIR)/host-build.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/pybind11
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Seamless operability between C++11 and Python
	DEPENDS:=+python3
	URL:=https://github.com/pybind/pybind11
endef

define Package/pybind11/description
	pybind11 is a lightweight header-only library that exposes C++ types in Python and vice versa, mainly to create Python bindings of existing C++ code.
endef

CMAKE_OPTIONS += \
	-Wno-dev \
	-DPYTHON_EXECUTABLE="$(STAGING_DIR_HOSTPKG)/bin/$(PYTHON3)"

define Package/pybind11/install
	$(INSTALL_DIR) \
	  $(1)/$(PYTHON3_PKG_DIR)

	$(CP) \
	  $(PKG_INSTALL_DIR)/$(PYTHON3_PKG_DIR)/pybind11/*.py* \
	  $(1)/$(PYTHON3_PKG_DIR)/pybind11/
endef

$(eval $(call BuildPackage,pybind11))
$(eval $(call HostBuild))
