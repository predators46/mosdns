include $(TOPDIR)/rules.mk

PKG_NAME:=python-cppy
PKG_VERSION:=1.2.1
PKG_RELEASE:=1

PYPI_NAME:=cppy
PKG_HASH:=83b43bf17b1085ac15c5debdb42154f138b928234b21447358981f69d0d6fe1b

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=python-setuptools-scm/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-cppy
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=A collection of C++ headers which make it easier to write Python C extension modules.
  URL:=https://github.com/nucleic/cppy
  DEPENDS:=+python3
endef

define Package/python3-cppy/description
  A small C++ header library which makes it easier to write Python extension modules.
  The primary feature is a PyObject smart pointer which automatically handles reference counting and provides convenience methods for performing common object operations.
endef

$(eval $(call Py3Package,python3-cppy))
$(eval $(call BuildPackage,python3-cppy))
$(eval $(call BuildPackage,python3-cppy-src))
