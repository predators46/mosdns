include $(TOPDIR)/rules.mk

PKG_NAME:=badvpn
PKG_VERSION:=1.999.130
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/ambrop72/badvpn/tar.gz/$(PKG_VERSION)?
PKG_HASH:=bfd4bbfebd7274bcec792558c9a2fd60e39cd92e04673825ade5d04154766109

PKG_MAINTAINER:=Andy Syam <privasisource@gmail.com>
PKG_LICENSE:=LICENSE
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DIR:=$(BUILD_DIR)/badvpn-$(PKG_VERSION)

CMAKE_SOURCE_DIR:=build

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/badvpn
	SECTION:=net
	CATEGORY:=Network
	TITLE:=NCD scripting language, tun2socks proxifier, P2P VPN
	DEPENDS:=+librt +libpthread +libudev-zero +libnss +libopenssl +coreutils +coreutils-stdbuf +openssl-util
	URL:=https://github.com/ambrop72/badvpn
endef

define Package/badvpn/description
  Peer-to-peer VPN system, and NCD, a programming language for network interface configuration
endef

CMAKE_OPTIONS += \
	-DBUILD_NOTHING_BY_DEFAULT=1 \
	-DBUILD_TUN2SOCKS=1 \
	-DBUILD_UDPGW=1

define Package/badvpn/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tun2socks/badvpn-tun2socks $(1)/usr/bin/badvpn-tun2socks
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/udpgw/badvpn-udpgw $(1)/usr/bin/badvpn-udpgw
endef

$(eval $(call BuildPackage,badvpn))
