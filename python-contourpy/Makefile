include $(TOPDIR)/rules.mk

PKG_NAME:=python-contourpy
PKG_VERSION:=1.2.1
PKG_RELEASE:=1

PYPI_NAME:=contourpy
PKG_HASH:=4d8908b3bee1c889e547867ca4cdc54e5ab6be6d3e078556814a22457f49423c

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python-setuptools-scm/host python-pybind11
PKG_BUILD_DEPENDS:=python-setuptools-scm/host python-pybind11

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/python3-contourpy
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python library for calculating contours of 2D quadrilateral grids
  URL:=https://github.com/contourpy/contourpy
  DEPENDS:=+python3 +python3-numpy
endef

define Package/python3-contourpy/description
  ContourPy is a Python library for calculating contours of 2D quadrilateral grids.
  It is written in C++11 and wrapped using pybind11.
endef

$(eval $(call Py3Package,python3-contourpy))
$(eval $(call BuildPackage,python3-contourpy))
$(eval $(call BuildPackage,python3-contourpy-src))
$(eval $(call HostBuild))
