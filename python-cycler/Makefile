include $(TOPDIR)/rules.mk

PKG_NAME:=python-cycler
PKG_VERSION:=0.12.1
PKG_RELEASE:=1

PYPI_NAME:=cycler
PKG_HASH:=88bb128f02ba341da8ef447245a9e138fae777f6a23943da4540077d3601eb1c

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python-setuptools-scm/host
PKG_BUILD_DEPENDS:=python-setuptools-scm/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/python3-cycler
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=cycler: composable cycles
  URL:=https://github.com/matplotlib/cycler
  DEPENDS:=+python3
endef

define Package/python3-cycler/description
  Composable style cycles in Python
endef

$(eval $(call Py3Package,python3-cycler))
$(eval $(call BuildPackage,python3-cycler))
$(eval $(call BuildPackage,python3-cycler-src))
$(eval $(call HostBuild))
