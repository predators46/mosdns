include $(TOPDIR)/rules.mk

PKG_NAME:=einat-ebpf
PKG_VERSION:=0.1.2
PKG_RELEASE:=5

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/EHfive/einat-ebpf/tar.gz/refs/tags/v$(PKG_VERSION)?
PKG_HASH:=17bb289475687cb6970415afc35c374ea80cd01e59964f2f9a611f6fe88f4270

PKG_MAINTAINER:=Anya Lin <hukk1996@gmail.com>
PKG_LICENSE:=GPL-2.0-or-later GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
#include $(INCLUDE_DIR)/bpf.mk
include $(TOPDIR)/feeds/packages/xorg/rust/rust-package.mk

define Package/einat-ebpf
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  TITLE:=eBPF-based Endpoint-Independent NAT
  URL:=https://github.com/EHfive/einat-ebpf
  # You need enable KERNEL_DEBUG_INFO_BTF and disable KERNEL_DEBUG_INFO_REDUCED
  DEPENDS:=$(RUST_ARCH_DEPENDS) $(BPF_DEPENDS) +libelf +zlib +kmod-sched-core +kmod-sched-bpf
  USERID:=einat:einat
  PROVIDES:=einat
endef

define Package/einat-ebpf/description
  This eBPF application implements an "Endpoint-Independent Mapping" and
  "Endpoint-Independent Filtering" NAT(network address translation) on
  TC egress and ingress hooks.
endef

define Package/einat-ebpf/conffiles
/etc/config/einat
endef

define Package/einat-ebpf/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/einat $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) $(CURDIR)/files/einat.init $(1)/etc/init.d/einat

	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_CONF) $(CURDIR)/files/einat.config $(1)/etc/config/einat

	$(INSTALL_DIR) $(1)/etc/capabilities/
	$(INSTALL_CONF) $(CURDIR)/files/capabilities.json $(1)/etc/capabilities/einat.json
endef

$(eval $(call RustBinPackage,einat-ebpf))
$(eval $(call BuildPackage,einat-ebpf))
