include $(TOPDIR)/rules.mk

PKG_NAME:=python-mako
PKG_VERSION:=1.3.2
PKG_RELEASE:=1

PYPI_NAME:=Mako
PKG_HASH:=2a0c8ad7f6274271b3bb7467dd37cf9cc6dab4bc19cb69a4ef10669402de698e

PKG_MAINTAINER:=
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_FLAGS:=no-mips16

HOST_BUILD_DEPENDS:=python-setuptools-scm/host python-wheel/host python-markupsafe/host
PKG_BUILD_DEPENDS:=python-setuptools-scm/host python-wheel/host python-markupsafe/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

define Package/python3-mako
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=A super-fast templating language that borrows the best ideas from the existing templating languages.
  URL:=https://github.com/sqlalchemy/mako
  DEPENDS:=+python3-light +python-markupsafe
endef

define Package/python3-mako/description
  Mako is a template library written in Python. It provides a familiar, non-XML syntax which compiles into Python modules for maximum performance. Mako’s syntax and API borrows from the best ideas of many others, including Django templates, Cheetah, Myghty, and Genshi. Conceptually, Mako is an embedded Python (i.e. Python Server Page) language, which refines the familiar ideas of componentized layout and inheritance to produce one of the most straightforward and flexible models available, while also maintaining close ties to Python calling and scoping semantics.
endef

$(eval $(call Py3Package,python3-mako))
$(eval $(call BuildPackage,python3-mako))
$(eval $(call BuildPackage,python3-mako-src))
$(eval $(call HostBuild))
