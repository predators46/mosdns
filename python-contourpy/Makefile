include $(TOPDIR)/rules.mk

PKG_NAME:=python-contourpy
PKG_VERSION:=1.3.0
PKG_RELEASE:=1

PYPI_NAME:=contourpy
PKG_HASH:=7ffa0db17717a8ffb127efd0c95a4362d996b892c2904db72428d5b52e1938a4

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python-setuptools-scm/host python-pybind11/host meson/host meson-python/host
PKG_BUILD_DEPENDS:=python-setuptools-scm/host python-pybind11/host meson/host meson-python/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/meson.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/python3-contourpy
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python library for calculating contours of 2D quadrilateral grids
  URL:=https://github.com/contourpy/contourpy
  DEPENDS:=+python3 +python3-numpy +meson +meson-python
endef

define Package/python3-contourpy/description
  ContourPy is a Python library for calculating contours of 2D quadrilateral grids.
  It is written in C++11 and wrapped using pybind11.
endef

define Meson/CreateNativeFile
	$(STAGING_DIR_HOST)/bin/sed \
		-e "s|@CC@|$(foreach BIN,$(HOSTCC),'$(BIN)',)|" \
		-e "s|@CXX@|$(foreach BIN,$(HOSTCXX),'$(BIN)',)|" \
		-e "s|@PKGCONFIG@|$(PKG_CONFIG)|" \
		-e "s|@CMAKE@|$(STAGING_DIR_HOST)/bin/cmake|" \
		-e "s|@PYTHON@|$(STAGING_DIR_HOSTPKG)/bin/python3|" \
		-e "s|@CFLAGS@|$(foreach FLAG,$(HOST_CFLAGS) $(HOST_CPPFLAGS),'$(FLAG)',)|" \
		-e "s|@CXXFLAGS@|$(foreach FLAG,$(HOST_CXXFLAGS) $(HOST_CPPFLAGS),'$(FLAG)',)|" \
		-e "s|@LDFLAGS@|$(foreach FLAG,$(HOST_LDFLAGS),'$(FLAG)',)|" \
		-e "s|@PREFIX@|$(HOST_BUILD_PREFIX)|" \
		< $(MESON_DIR)/openwrt-native.txt.in \
		> $(1)
endef

define Meson/CreateCrossFile
	$(STAGING_DIR_HOST)/bin/sed \
		-e "s|@CC@|$(foreach BIN,$(TARGET_CC),'$(BIN)',)|" \
		-e "s|@CXX@|$(foreach BIN,$(TARGET_CXX),'$(BIN)',)|" \
		-e "s|@LD@|$(foreach FLAG,$(TARGET_LINKER),'$(FLAG)',)|" \
		-e "s|@AR@|$(TARGET_AR)|" \
		-e "s|@STRIP@|$(TARGET_CROSS)strip|" \
		-e "s|@NM@|$(TARGET_NM)|" \
		-e "s|@PKGCONFIG@|$(PKG_CONFIG)|" \
		-e "s|@CMAKE@|$(STAGING_DIR_HOST)/bin/cmake|" \
		-e "s|@PYTHON@|$(STAGING_DIR_HOSTPKG)/bin/python3|" \
		-e "s|@CFLAGS@|$(foreach FLAG,$(TARGET_CFLAGS) $(EXTRA_CFLAGS) $(TARGET_CPPFLAGS) $(EXTRA_CPPFLAGS),'$(FLAG)',)|" \
		-e "s|@CXXFLAGS@|$(foreach FLAG,$(TARGET_CXXFLAGS) $(EXTRA_CXXFLAGS) $(TARGET_CPPFLAGS) $(EXTRA_CPPFLAGS),'$(FLAG)',)|" \
		-e "s|@LDFLAGS@|$(foreach FLAG,$(TARGET_LDFLAGS) $(EXTRA_LDFLAGS),'$(FLAG)',)|" \
		-e "s|@ARCH@|$(MESON_ARCH)|" \
		-e "s|@CPU@|$(MESON_CPU)|" \
		-e "s|@ENDIAN@|$(if $(CONFIG_BIG_ENDIAN),big,little)|" \
		< $(MESON_DIR)/openwrt-cross.txt.in \
		> $(1)
endef

$(eval $(call Py3Package,python3-contourpy))
$(eval $(call BuildPackage,python3-contourpy))
$(eval $(call BuildPackage,python3-contourpy-src))
$(eval $(call HostBuild))
