include $(TOPDIR)/rules.mk

PKG_NAME:=python-meson-python
PKG_VERSION:=0.16.0
PKG_RELEASE:=1

PYPI_NAME:=meson_python
PKG_HASH:=9068c17e36c89d6c7ff709fffb2a8a9925e8cd0b02629728e5ceaf2ec505cb5f

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python-setuptools-scm/host pyproject-metadata/host python-packaging/host python-tomli/host
PKG_BUILD_DEPENDS:=python-setuptools-scm/host pyproject-metadata/host python-packaging/host python-tomli/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/meson.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/python3-meson-python
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Meson Python build backend (PEP 517)
  URL:=https://github.com/mesonbuild/meson-python
  DEPENDS:=+python3 +python3-pyproject-metadata +python3-packaging +python3-tomli
endef

define Package/python3-meson-python/description
  meson-python is a Python build back-end built on top of the Meson build system.
  It enables using Meson for the configuration and build steps of Python packages.
  Meson is an open source build system meant to be both extremely fast, and, even more importantly, as user friendly as possible.
  meson-python is best suited for building Python packages containing extension modules implemented in languages such as C, C++, Cython, Fortran, Pythran, or Rust. Consult the documentation for more details.
endef

$(eval $(call Py3Package,python3-meson-python))
$(eval $(call BuildPackage,python3-meson-python))
$(eval $(call BuildPackage,python3-meson-python-src))
$(eval $(call HostBuild))
