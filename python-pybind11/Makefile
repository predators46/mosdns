include $(TOPDIR)/rules.mk

PKG_NAME:=python-pybind11
PKG_VERSION:=2.13.5
PKG_RELEASE:=1

#PYPI_NAME:=pybind11
#PKG_HASH:=ae33f635322f9d9741abde0c5f348bf9373f6c22298883395e586cb43c55574e

PKG_SOURCE:=pybind11-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/pybind/pybind11/archive/v$(PKG_VERSION)
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/pybind11-$(PKG_VERSION)

HOST_BUILD_DEPENDS:=python-setuptools-scm/host boost
PKG_BUILD_DEPENDS:=python-setuptools-scm/host boost

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/cmake.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/python3-pybind11
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Seamless operability between C++11 and Python
  URL:=https://github.com/pybind/pybind11
  DEPENDS:=+python3 +python3-setuptools
endef

define Package/python3-pybind11/description
  pybind11 is a lightweight header-only library that exposes C++ types in Python and vice versa, mainly to create Python bindings of existing C++ code.
endef

CMAKE_OPTIONS += \
	-DPYBIND11_TEST=OFF

$(eval $(call Py3Package,python3-pybind11))
$(eval $(call BuildPackage,python3-pybind11))
$(eval $(call BuildPackage,python3-pybind11-src))
$(eval $(call HostBuild))
