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
PKG_BUILD_DEPENDS:=python-setuptools-scm/host python-pytest/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(INCLUDE_DIR)/host-build.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/pybind11
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Seamless operability between C++11 and Python
	DEPENDS:=+python3 +python3-setuptools
	URL:=https://github.com/pybind/pybind11
endef

define Package/pybind11/description
	pybind11 is a lightweight header-only library that exposes C++ types in Python and vice versa, mainly to create Python bindings of existing C++ code.
endef

CMAKE_OPTIONS += \
	-Wno-dev \
	-DPYTHON_EXECUTABLE="$(STAGING_DIR_HOSTPKG)/bin/$(PYTHON3)" \
	-DPYTHON_INCLUDE_DIR="$(shell $(STAGING_DIR)/host/bin/$(PYTHON3)-config --includes)" \
	-DPYTHON_LIBRARY="$(shell $(STAGING_DIR)/host/bin/$(PYTHON3)-config --libs)"

define Build/Compile
	$(call Build/Compile/Default)
	$(call Py3Build/Compile)
endef

define Py3Package/pybind11/filespec
+|$(PYTHON3_PKG_DIR)
-|$(PYTHON3_PKG_DIR)/pybind11/include
-|$(PYTHON3_PKG_DIR)/pybind11/share
endef

$(eval $(call Py3Package,pybind11))
$(eval $(call BuildPackage,pybind11))
$(eval $(call BuildPackage,pybind11-src))
$(eval $(call HostBuild))
