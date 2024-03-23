include $(TOPDIR)/rules.mk

PKG_NAME:=tun2socks
PKG_VERSION:=2.5.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/xjasonlyu/tun2socks/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=48f42df4e991264196971035a63aa46647a41e031a60f4c4347a393ea43d9020

PKG_MAINTAINER:=
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/xjasonlyu/tun2socks/v2
GO_PKG_BUILD_PKG:=$(GO_PKG)
GO_PKG_LDFLAGS_X:=$(GO_PKG)/internal/version.version=v$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/mosdns/golang/golang-package.mk

define Package/tun2socks
  SECTION:=net
  CATEGORY:=Network
  TITLE:=tun2socks - powered by gVisor TCP/IP stack
  URL:=https://github.com/xjasonlyu/tun2socks
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle

endef

define Package/tun2socks/description
  Proxy Everything: Handle all network traffic of any internet programs sent by the device through a proxy.
  Proxy Protocols: HTTP/Socks4/Socks5/Shadowsocks with authentication support for remote connections.
  Run Everywhere: Linux/macOS/Windows/FreeBSD/OpenBSD multi-platform support with specific optimization.
  Gateway Mode: Act as a layer three gateway to handle network traffic from other devices in the same network.
  Full IPv6 Support: All functions work in IPv6, tunnel IPv4 connections through IPv6 proxy and vice versa.
  Network Stack: Powered by user-space TCP/IP stack from Google container application kernel gVisor.
endef

define Build/Compile
  $(call GoPackage/Build/Compile)
endef

define Package/tun2socks/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/tun2socks $(1)/usr/bin/

endef

$(eval $(call GoBinPackage,tun2socks))
$(eval $(call BuildPackage,tun2socks))
