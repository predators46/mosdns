include $(TOPDIR)/rules.mk

PKG_NAME:=python-kiwisolver
PKG_VERSION:=1.4.5
PKG_RELEASE:=1

PYPI_NAME:=kiwisolver
PKG_HASH:=e57e563a57fb22a142da34f38acc2fc1a5c864bc29ca1517a88abc963e60d6ec

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause-Attribution
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=python-setuptools-scm/host python-cppy

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-kiwisolver
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Efficient C++ implementation of the Cassowary constraint solving algorithm
  URL:=https://github.com/nucleic/kiwi
  DEPENDS:=+python3 +libstdcpp +python3-cppy
endef

define Package/python3-kiwisolver/description
  Kiwi is an efficient C++ implementation of the Cassowary constraint solving algorithm.
  Kiwi is an implementation of the algorithm based on the seminal Cassowary paper.
  It is not a refactoring of the original C++ solver. Kiwi has been designed from the ground up to be lightweight and fast.
  Kiwi ranges from 10x to 500x faster than the original Cassowary solver with typical use cases gaining a 40x improvement.
  Memory savings are consistently > 5x.
endef

$(eval $(call Py3Package,python3-kiwisolver))
$(eval $(call BuildPackage,python3-kiwisolver))
$(eval $(call BuildPackage,python3-kiwisolver-src))
