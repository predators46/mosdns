include $(TOPDIR)/rules.mk

PKG_NAME:=python-tomli
PKG_VERSION:=2.0.1
PKG_RELEASE:=1

PYPI_NAME:=tomli
PKG_HASH:=de526c12914f0c550d15924c62d72abc48d6fe7364aa87328337a31007fe8a4f

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python-setuptools-scm/host python-flit-core/host
PKG_BUILD_DEPENDS:=python-setuptools-scm/host python-flit-core/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/python3-tomli
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=A lil' TOML parser
  URL:=https://github.com/hukkin/tomli
  DEPENDS:=+python3 +python3-flit-core
endef

define Package/python3-tomli/description
  Tomli is a Python library for parsing TOML. It is fully compatible with TOML v1.0.0.
  A version of Tomli, the tomllib module, was added to the standard library in Python 3.11 via PEP 680.
  Tomli continues to provide a backport on PyPI for Python versions where the standard library module is not available and that have not yet reached their end-of-life.
endef

$(eval $(call Py3Package,python3-tomli))
$(eval $(call BuildPackage,python3-tomli))
$(eval $(call BuildPackage,python3-tomli-src))
$(eval $(call HostBuild))
