include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-mosdns
PKG_VERSION:=778
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0

PKG_MAINTAINER:=

#PKG_BUILD_DEPENDS:=python3/host
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-mosdns
  SECTION:=net
  CATEGORY:=Network
  #DEPENDS:=perl perl-html-tagset perl-net-dns perl-ack perl-html-tree perl-net-http perl-authen-sasl perl-http-cookies perl-net-telnet perl-authen-sasl-xs perl-http-daemon perl-parse-recdescent perl-cgi perl-http-date perl-parse-yapp perl-compress-bzip2 perl-http-message perl-sub-uplevel perl-dbi perl-http-negotiate perl-test-harness perl-device-serialport perl-http-server-simple perl-test-warn perl-device-usb perl-inline perl-text-csv_xs perl-encode-locale perl-inline-c perl-try-tiny perl-file-listing perl-io-html perl-uri perl-file-next perl-lockfile-simple perl-www perl-file-rsyncp perl-lwp-mediatypes perl-www-curl perl-file-sharedir-install perl-www-mechanize perl-html-form perl-netaddr-ip perl-www-robotrules perl-html-parser perl-net-cidr-lite perl-xml-parser spamassassin spamc spamc-ssl
  #DEPENDS:=+qtbase +qtcharts +qtgamepad +qttools +qtmultimedia +qtnetworkauth +qtconnectivity +qtpurchasing +qtlocation +qtremoteobjects +qtserialport +qtserialbus +qtsensors +qtsvg +qtscript +qtspeech +qtwebsockets +qtwebchannel +qtxmlpatterns +qttranslations
  #DEPENDS:=freeradius3 freeradius3-common freeradius3-default freeradius3-democerts freeradius3-mod-always freeradius3-mod-attr-filter freeradius3-mod-cache freeradius3-mod-cache-rbtree freeradius3-mod-cache-redis freeradius3-mod-chap freeradius3-mod-counter freeradius3-mod-date freeradius3-mod-detail freeradius3-mod-digest freeradius3-mod-dpsk freeradius3-mod-dynamic-clients freeradius3-mod-eap freeradius3-mod-eap-fast freeradius3-mod-eap-gtc freeradius3-mod-eap-md5 freeradius3-mod-eap-mschapv2 freeradius3-mod-eap-peap freeradius3-mod-eap-pwd freeradius3-mod-eap-sim freeradius3-mod-eap-tls freeradius3-mod-eap-ttls freeradius3-mod-exec freeradius3-mod-expiration freeradius3-mod-expr freeradius3-mod-files freeradius3-mod-ippool freeradius3-mod-json freeradius3-mod-krb5 freeradius3-mod-ldap freeradius3-mod-linelog freeradius3-mod-logintime freeradius3-mod-mschap freeradius3-mod-pam freeradius3-mod-pap freeradius3-mod-passwd freeradius3-mod-preprocess freeradius3-mod-python3 freeradius3-mod-radutmp freeradius3-mod-realm freeradius3-mod-redis freeradius3-mod-rediswho freeradius3-mod-replicate freeradius3-mod-rest freeradius3-mod-soh freeradius3-mod-sometimes freeradius3-mod-sql freeradius3-mod-sql-map freeradius3-mod-sql-mysql freeradius3-mod-sql-null freeradius3-mod-sql-postgresql freeradius3-mod-sql-sqlite freeradius3-mod-sql-unixodbc freeradius3-mod-sqlcounter freeradius3-mod-sqlippool freeradius3-mod-totp freeradius3-mod-unbound freeradius3-mod-unix freeradius3-mod-unpack freeradius3-mod-utf8 freeradius3-mod-wimax freeradius3-mod-yubikey freeradius3-utils
  #DEPENDS:=+freeradius3 +freeradius3-common +freeradius3-default +freeradius3-democerts +freeradius3-mod-always +freeradius3-mod-attr-filter +freeradius3-mod-cache +freeradius3-mod-cache-rbtree +freeradius3-mod-cache-redis +freeradius3-mod-chap +freeradius3-mod-counter +freeradius3-mod-date +freeradius3-mod-detail +freeradius3-mod-digest +freeradius3-mod-dpsk +freeradius3-mod-dynamic-clients +freeradius3-mod-eap +freeradius3-mod-eap-fast +freeradius3-mod-eap-gtc +freeradius3-mod-eap-md5 +freeradius3-mod-eap-mschapv2 +freeradius3-mod-eap-peap +freeradius3-mod-eap-pwd +freeradius3-mod-eap-sim +freeradius3-mod-eap-tls +freeradius3-mod-eap-ttls +freeradius3-mod-exec +freeradius3-mod-expiration +freeradius3-mod-expr +freeradius3-mod-files +freeradius3-mod-ippool +freeradius3-mod-json +freeradius3-mod-krb5 +freeradius3-mod-ldap +freeradius3-mod-linelog +freeradius3-mod-logintime +freeradius3-mod-mschap +freeradius3-mod-pam +freeradius3-mod-pap +freeradius3-mod-passwd +freeradius3-mod-preprocess +freeradius3-mod-python3 +freeradius3-mod-radutmp +freeradius3-mod-realm +freeradius3-mod-redis +freeradius3-mod-rediswho +freeradius3-mod-replicate +freeradius3-mod-rest +freeradius3-mod-soh +freeradius3-mod-sometimes +freeradius3-mod-sql +freeradius3-mod-sql-map +freeradius3-mod-sql-mysql +freeradius3-mod-sql-null +freeradius3-mod-sql-postgresql +freeradius3-mod-sql-sqlite +freeradius3-mod-sql-unixodbc +freeradius3-mod-sqlcounter +freeradius3-mod-sqlippool +freeradius3-mod-totp +freeradius3-mod-unbound +freeradius3-mod-unix +freeradius3-mod-unpack +freeradius3-mod-utf8 +freeradius3-mod-wimax +freeradius3-mod-yubikey +freeradius3-utils
  DEPENDS:=libncurses
  TITLE:=Tools Inject xderm-mini
endef

define Package/luci-app-mosdns/description
 xderm-mini ssh v2ray trojan
endef

define Build/Prepare
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/luci-app-mosdns/install
endef

$(eval $(call BuildPackage,luci-app-mosdns))
