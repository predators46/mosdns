include $(TOPDIR)/rules.mk

PKG_NAME:=python-tun2socks
PKG_VERSION:=2.5.2.1
PKG_RELEASE:=1

PYPI_NAME:=tun2socks
PKG_HASH:=c24f0b1c538355db2da9a3af18b574b1a0bb7a00616557005e8ca4e30441c2c1

PKG_LICENSE:=GPL-3.0 license
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=

PKG_BUILD_DEPENDS:=python-setuptools-scm/host golang/host

#GO_PKG:=github.com/xjasonlyu/tun2socks/v2
#GO_PKG_BUILD_PKG:=$(GO_PKG)
GO_PKG_LDFLAGS_X:=$(GO_PKG)/internal/version.version=v$(PKG_VERSION)

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(TOPDIR)/feeds/mosdns/golang/golang-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-tun2socks
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Tun2socks Python
  URL:=https://github.com/LorenEteval/tun2socks-python
  DEPENDS:=+python3-light
endef

define Package/python3-tun2socks/description
Python bindings for go tun2socks.
endef

MAKE_VARS += \
	GO_INSTALL_BIN_PATH="$(strip $(GO_PKG_INSTALL_BIN_PATH))" \
	BUILD_DIR="$(PKG_BUILD_DIR)" \
	GO_BUILD_DIR="$(GO_PKG_BUILD_DIR)" \
	GO_BUILD_BIN_DIR="$(GO_PKG_BUILD_BIN_DIR)" \
	GO_BUILD_DEPENDS_PATH="$(GO_PKG_BUILD_DEPENDS_PATH)" \
	GO_BUILD_DEPENDS_SRC="$(GO_PKG_BUILD_DEPENDS_SRC)" \
	GOOS="$(GO_OS)" \
	GOARCH="$(GO_ARCH)" \
	CC="$(TARGET_CC)" \
	CXX="$(TARGET_CXX)" \
	CGO_CFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CFLAGS))" \
	CGO_CPPFLAGS="$(TARGET_CPPFLAGS)" \
	CGO_CXXFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CXXFLAGS))" \
	CGO_LDFLAGS="$(TARGET_LDFLAGS)" \
	GOPATH="$(GO_PKG_BUILD_DIR)" \
	GOCACHE="$(GO_BUILD_CACHE_DIR)" \
	GOMODCACHE="$(GO_MOD_CACHE_DIR)" \
	GOFLAGS="$(GO_PKG_GCFLAGS)" \
	GO_PKG_CFLAGS="$(GO_PKG_CFLAGS)" \
	CGO_ENABLED=1 \
	GOENV=off \
	EXTRA_LDFLAGS="$(GO_PKG_LDFLAGS)"

$(eval $(call Py3Package,python3-tun2socks))
$(eval $(call BuildPackage,python3-tun2socks))
$(eval $(call BuildPackage,python3-tun2socks-src))
