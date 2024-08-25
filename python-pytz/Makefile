include $(TOPDIR)/rules.mk

PKG_NAME:=python-pytz
PKG_VERSION:=2024.1
PKG_RELEASE:=1

PYPI_NAME:=pytz
PKG_HASH:=2a29735ea9c18baf14b448846bde5a48030ed267578472d8955cd0e7443a9812

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE.txt

PKG_BUILD_DEPENDS:=python-setuptools-scm/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-pytz
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python3 definitions of world timezone
  URL:=https://pythonhosted.org/pytz/
  DEPENDS:=+python3
endef

define Package/python3-pytz/description
  pytz brings the Olson tz database into Python. This library allows accurate and cross platform timezone calculations using Python 2.4 or higher.
  It also solves the issue of ambiguous times at the end of daylight saving time, which you can read more about in the Python Library Reference (datetime.tzinfo).
endef

$(eval $(call Py3Package,python3-pytz))
$(eval $(call BuildPackage,python3-pytz))
$(eval $(call BuildPackage,python3-pytz-src))
