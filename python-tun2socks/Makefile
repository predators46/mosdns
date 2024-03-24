include $(TOPDIR)/rules.mk

PKG_NAME:=python-tun2socks
PKG_VERSION:=2.5.2.1
PKG_RELEASE:=1

PYPI_NAME:=tun2socks
PKG_HASH:=c24f0b1c538355db2da9a3af18b574b1a0bb7a00616557005e8ca4e30441c2c1

PKG_LICENSE:=GPL-3.0 license
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=

PKG_BUILD_DEPENDS:=python-setuptools-scm/host python-wheel/host golang/host

GO_PKG_TARGET_VARS:= \
	GOOS="$(GO_OS)" \
	GOARCH="$(GO_ARCH)" \
	GO386="$(GO_386)" \
	GOAMD64="$(GO_AMD64)" \
	GOARM="$(GO_ARM)" \
	GOMIPS="$(GO_MIPS)" \
	GOMIPS64="$(GO_MIPS64)" \
	GOPPC64="$(GO_PPC64)" \
	CGO_ENABLED=1 \
	CC="$(TARGET_CC)" \
	CXX="$(TARGET_CXX)" \
	CGO_CFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CFLAGS))" \
	CGO_CPPFLAGS="$(TARGET_CPPFLAGS)" \
	CGO_CXXFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CXXFLAGS))" \
	CGO_LDFLAGS="$(TARGET_LDFLAGS)"

MAKE_VARS:= \
	GOOS="$(GO_OS)" \
	GOARCH="$(GO_ARCH)" \
	GO386="$(GO_386)" \
	GOAMD64="$(GO_AMD64)" \
	GOARM="$(GO_ARM)" \
	GOMIPS="$(GO_MIPS)" \
	GOMIPS64="$(GO_MIPS64)" \
	GOPPC64="$(GO_PPC64)" \
	CGO_ENABLED=1 \
	CC="$(TARGET_CC)" \
	CXX="$(TARGET_CXX)" \
	CGO_CFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CFLAGS))" \
	CGO_CPPFLAGS="$(TARGET_CPPFLAGS)" \
	CGO_CXXFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CXXFLAGS))" \
	CGO_LDFLAGS="$(TARGET_LDFLAGS)"

#GO_PKG:=github.com/xjasonlyu/tun2socks/v2
#GO_PKG_BUILD_PKG:=$(GO_PKG)
GO_PKG_LDFLAGS_X:=$(GO_PKG)/internal/version.Version=v$(PKG_VERSION)

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
  DEPENDS:=$(GO_ARCH_DEPENDS) +python3-light +python3-setuptools-scm +python3-wheel +python3-setuptools
endef

define Package/python3-tun2socks/description
Python bindings for go tun2socks.
endef

GO_PKG_TARGET_VARS += \
	GOOS="$(GO_OS)" \
	GOARCH="$(GO_ARCH)" \
	GO386="$(GO_386)" \
	GOAMD64="$(GO_AMD64)" \
	GOARM="$(GO_ARM)" \
	GOMIPS="$(GO_MIPS)" \
	GOMIPS64="$(GO_MIPS64)" \
	GOPPC64="$(GO_PPC64)" \
	CGO_ENABLED=1 \
	CC="$(TARGET_CC)" \
	CXX="$(TARGET_CXX)" \
	CGO_CFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CFLAGS))" \
	CGO_CPPFLAGS="$(TARGET_CPPFLAGS)" \
	CGO_CXXFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CXXFLAGS))" \
	CGO_LDFLAGS="$(TARGET_LDFLAGS)"

MAKE_VARS += \
	GOOS="$(GO_OS)" \
	GOARCH="$(GO_ARCH)" \
	GO386="$(GO_386)" \
	GOAMD64="$(GO_AMD64)" \
	GOARM="$(GO_ARM)" \
	GOMIPS="$(GO_MIPS)" \
	GOMIPS64="$(GO_MIPS64)" \
	GOPPC64="$(GO_PPC64)" \
	CGO_ENABLED=1 \
	CC="$(TARGET_CC)" \
	CXX="$(TARGET_CXX)" \
	CGO_CFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CFLAGS))" \
	CGO_CPPFLAGS="$(TARGET_CPPFLAGS)" \
	CGO_CXXFLAGS="$(filter-out $(GO_CFLAGS_TO_REMOVE),$(TARGET_CXXFLAGS))" \
	CGO_LDFLAGS="$(TARGET_LDFLAGS)"

$(eval $(call Py3Package,python3-tun2socks))
$(eval $(call BuildPackage,python3-tun2socks))
$(eval $(call BuildPackage,python3-tun2socks-src))
