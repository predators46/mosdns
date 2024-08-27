include $(TOPDIR)/rules.mk

PKG_NAME:=python-pybind11
PKG_VERSION:=2.13.5
PKG_RELEASE:=1

PYPI_NAME:=pybind11
PKG_HASH:=ae33f635322f9d9741abde0c5f348bf9373f6c22298883395e586cb43c55574e

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

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/$(PYTHON3_PKG_DIR)/pybind11/include/pybind11 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/$(PYTHON3_PKG_DIR)/pybind11/share/{pkgconfig,cmake} $(1)/usr/share/
	$(SED) 's,^\(prefix\)=.*,\1=$(STAGING_DIR)/usr,g' $(1)/usr/share/pkgconfig/pybind11.pc
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/pybind11-config $(1)/usr/bin/
	$(INSTALL_DIR) $(2)/bin
	$(LN) ../../usr/bin/pybind11-config $(2)/bin/pybind11-config
endef

$(eval $(call Py3Package,python3-pybind11))
$(eval $(call BuildPackage,python3-pybind11))
$(eval $(call BuildPackage,python3-pybind11-src))
$(eval $(call HostBuild))
