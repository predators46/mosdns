include $(TOPDIR)/rules.mk

PKG_NAME:=python-tun2socks
PKG_VERSION:=2.5.2.1
PKG_RELEASE:=1

PYPI_NAME:=tun2socks
PKG_HASH:=c24f0b1c538355db2da9a3af18b574b1a0bb7a00616557005e8ca4e30441c2c1

PKG_LICENSE:=GPL-3.0 license
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=

PKG_BUILD_DEPENDS:=python-setuptools-scm/host

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(TOPDIR)/feeds/mosdns/golang/golang-package.mk
include ../python3-package.mk

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

$(eval $(call Py3Package,python3-tun2socks))
$(eval $(call BuildPackage,python3-tun2socks))
$(eval $(call BuildPackage,python3-tun2socks-src))
