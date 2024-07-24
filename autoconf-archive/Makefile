include $(TOPDIR)/rules.mk

PKG_NAME:=autoconf-archive
PKG_VERSION:=2023.02.20

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=@GNU/autoconf-archive
PKG_HASH:=71d4048479ae28f1f5794619c3d72df9c01df49b1c628ef85fde37596dc31a33

PKG_LICENSE:=GPL-3.0 License
PKG_LICENSE_FILES:=COPYING COPYING.EXCEPTION
PKG_MAINTAINER:=Andy Syam <privasisource@gmail.com>

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/autoconf-archive
  SECTION:=devel
  CATEGORY:=Development
  TITLE:=GNU Autoconf Archive
  URL:=https://github.com/autoconf-archive/autoconf-archive
endef

define Package/autoconf-archive/description
  Collection of re-usable GNU Autoconf macros
endef

define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR_HOST)/share
	$(CP) $(HOST_BUILD_DIR)/share/aclocal $(STAGING_DIR_HOST)/share/
endef

define Host/Uninstall
	-$(call Host/Compile/Default,uninstall)
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,autoconf-archive))
