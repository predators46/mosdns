include $(TOPDIR)/rules.mk

PKG_NAME:=python-pycairo
PKG_VERSION:=1.26.1
PKG_RELEASE:=1

PYPI_NAME:=pycairo
PKG_HASH:=a11b999ce55b798dbf13516ab038e0ce8b6ec299b208d7c4e767a6f7e68e8430

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=License LGPL-2.1
PKG_LICENSE_FILES:=COPYING-LGPL-2.1 COPYING-MPL-1.1

#PKG_BUILD_DEPENDS:=python-setuptools-scm/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

MESON_ARGS += -Dtests=false -Dwheel=false

define Package/python3-pycairo
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python bindings for cairo
  URL:=https://github.com/pygobject/pycairo
  DEPENDS:=+python3 +libcairo
endef

define Package/python3-pycairo/description
  Pycairo is a Python module providing bindings for the cairo graphics library.
endef

$(eval $(call Py3Package,python3-pycairo))
$(eval $(call BuildPackage,python3-pycairo))
$(eval $(call BuildPackage,python3-pycairo-src))
