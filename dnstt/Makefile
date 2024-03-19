include $(TOPDIR)/rules.mk

PKG_NAME:=dnstt
PKG_VERSION:=v1.20220208.0
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://www.bamsoftware.com/git/dnstt.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=dnstt-$(PKG_VERSION)
GO_PKG_BUILD_PKG:=$(GO_PKG)/dnstt-client

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/mosdns/golang/golang-package.mk

define Package/dnstt-client
  SECTION:=net
  CATEGORY:=Network
  TITLE:=DNS tunnel that can use DNS-over-HTTPS and DNS-over-TLS resolvers.
  URL:=https://www.bamsoftware.com/software/dnstt/
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
endef

define Package/dnstt-client/description
  dnstt uses end-to-end encryption and authentication between the tunnel client and tunnel server by default.
  Its protocol design enables higher performance than other DNS tunnels.
endef

define Package/dnstt-client/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/dnstt-client $(1)/usr/bin/
endef

$(eval $(call BuildPackage,dnstt-client))
