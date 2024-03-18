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

include $(INCLUDE_DIR)/package.mk

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

define Build/Configure
	echo -e \
	"SET(CMAKE_SYSTEM_NAME Linux)\n" \
	"SET(CMAKE_C_COMPILER $(TARGET_CC))\n" \
	"SET(CMAKE_CXX_COMPILER $(TARGET_CXX))\n" \
	"SET(CMAKE_FIND_ROOT_PATH $(STAGING_DIR) $(STAGING_DIR_HOST))\n" \
	> "$(PKG_BUILD_DIR)/toolchain.cmake"
	(cd $(PKG_BUILD_DIR); \
		CFLAGS="$(TARGET_CFLAGS)" \
		LDFLAGS="$(TARGET_LDFLAGS)" \
		cmake . \
		-DCMAKE_TOOLCHAIN_FILE=$(PKG_BUILD_DIR)/toolchain.cmake \
		-DBUILD_NOTHING_BY_DEFAULT=1 \
		-DBUILD_TUN2SOCKS=1 \
		-DBUILD_UDPGW=1 \
	);
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)
endef

define Package/badvpn/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tun2socks/badvpn-tun2socks $(1)/usr/bin/badvpn-tun2socks
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/udpgw/badvpn-udpgw $(1)/usr/bin/badvpn-udpgw
endef

$(eval $(call BuildPackage,badvpn))
