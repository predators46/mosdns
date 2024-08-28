include $(TOPDIR)/rules.mk

PKG_NAME:=meson-python
PKG_VERSION:=0.16.0
PKG_RELEASE:=1

PYPI_NAME:=meson_python
PKG_HASH:=9068c17e36c89d6c7ff709fffb2a8a9925e8cd0b02629728e5ceaf2ec505cb5f

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python-setuptools-scm/host pyproject-metadata/host python-packaging/host python-tomli/host python-cython/host meson/host
PKG_BUILD_DEPENDS:=python-setuptools-scm/host pyproject-metadata/host python-packaging/host python-tomli/host python-cython/host meson/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/meson.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/meson-python
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Meson Python build backend (PEP 517)
  URL:=https://github.com/mesonbuild/meson-python
  DEPENDS:=+python3 +python3-pyproject-metadata +python3-packaging +python3-tomli +python3-setuptools +meson
endef

define Package/meson-python/description
  meson-python is a Python build back-end built on top of the Meson build system.
  It enables using Meson for the configuration and build steps of Python packages.
  Meson is an open source build system meant to be both extremely fast, and, even more importantly, as user friendly as possible.
  meson-python is best suited for building Python packages containing extension modules implemented in languages such as C, C++, Cython, Fortran, Pythran, or Rust. Consult the documentation for more details.
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

$(eval $(call Py3Package,meson-python))
$(eval $(call BuildPackage,meson-python))
$(eval $(call BuildPackage,meson-python-src))
$(eval $(call HostBuild))
