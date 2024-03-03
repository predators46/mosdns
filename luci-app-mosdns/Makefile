include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-mosdns
PKG_VERSION:=1.5.17
PKG_RELEASE:=1

LUCI_TITLE:=LuCI Support for mosdns
LUCI_PKGARCH:=all
LUCI_DEPENDS:=mysql coova-chilli freeradius3 freeradius3-common freeradius3-default freeradius3-democerts freeradius3-mod-always freeradius3-mod-attr-filter freeradius3-mod-cache freeradius3-mod-cache-rbtree freeradius3-mod-chap freeradius3-mod-counter freeradius3-mod-date freeradius3-mod-detail freeradius3-mod-digest freeradius3-mod-dynamic-clients freeradius3-mod-eap freeradius3-mod-eap-fast freeradius3-mod-eap-gtc freeradius3-mod-eap-md5 freeradius3-mod-eap-mschapv2 freeradius3-mod-eap-peap freeradius3-mod-eap-pwd freeradius3-mod-eap-sim freeradius3-mod-eap-tls freeradius3-mod-eap-ttls freeradius3-mod-exec freeradius3-mod-expiration freeradius3-mod-expr freeradius3-mod-files freeradius3-mod-ippool freeradius3-mod-krb5 freeradius3-mod-ldap freeradius3-mod-linelog freeradius3-mod-logintime freeradius3-mod-mschap freeradius3-mod-pam freeradius3-mod-pap freeradius3-mod-passwd freeradius3-mod-preprocess freeradius3-mod-python3 freeradius3-mod-radutmp freeradius3-mod-realm freeradius3-mod-redisfreeradius3-mod-rediswho freeradius3-mod-replicate freeradius3-mod-rest freeradius3-mod-soh freeradius3-mod-sometimes freeradius3-mod-sql freeradius3-mod-sql-map freeradius3-mod-sql-mysql freeradius3-mod-sql-null freeradius3-mod-sql-postgresql freeradius3-mod-sql-sqlite freeradius3-mod-sql-unixodbc freeradius3-mod-sqlcounter freeradius3-mod-sqlippool freeradius3-mod-totp freeradius3-mod-unix freeradius3-mod-unpack freeradius3-mod-utf8 freeradius3-mod-wimax freeradius3-mod-yubikey freeradius3-utils

define Package/$(PKG_NAME)/conffiles
/etc/config/mosdns
/etc/mosdns/cache.dump
/etc/mosdns/config_custom.yaml
/etc/mosdns/rule
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
