include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-mosdns
PKG_VERSION:=1.5.81
PKG_RELEASE:=1

PKG_BUILD_DEPENDS:=qt5base/host
LUCI_TITLE:=LuCI Support for mosdns
LUCI_PKGARCH:=all
LUCI_DEPENDS:=
define Package/$(PKG_NAME)/conffiles
/etc/config/mosdns
/etc/mosdns/cache.dump
/etc/mosdns/config_custom.yaml
/etc/mosdns/rule
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
