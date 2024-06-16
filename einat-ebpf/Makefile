include $(TOPDIR)/rules.mk

PKG_NAME:=einat-ebpf
PKG_VERSION:=0.1.2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/EHfive/einat-ebpf.git
PKG_SOURCE_VERSION:=6cfe6d26b8a39fad793eefb82f9242fca79cf4bf
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=Anya Lin <hukk1996@gmail.com>
PKG_LICENSE:=GPL-2.0-or-later GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rustup/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/bpf.mk
include $(TOPDIR)/feeds/xorg/rustup/rust-values.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  TITLE:=eBPF-based Endpoint-Independent NAT
  URL:=https://github.com/EHfive/einat-ebpf
  # You need enable KERNEL_DEBUG_INFO_BTF and disable KERNEL_DEBUG_INFO_REDUCED
  DEPENDS:=@USE_MUSL $(RUST_ARCH_DEPENDS) $(BPF_DEPENDS) +libelf +zlib +kmod-sched-core +kmod-sched-bpf \
    +@KERNEL_DEBUG_FS +@KERNEL_DEBUG_INFO_BTF
  USERID:=einat:einat
  PROVIDES:=einat
endef

define Package/$(PKG_NAME)/description
  This eBPF application implements an "Endpoint-Independent Mapping" and
  "Endpoint-Independent Filtering" NAT(network address translation) on
  TC egress and ingress hooks.
endef

define Package/$(PKG_NAME)/config
	menu "Features configuration"
		depends on PACKAGE_einat-ebpf

		config EINAT_EBPF_IPV6
			bool "Enable IPV6 NAT66 feature"
			default n
			help
			  It would increase load time of eBPF programs to
			  about 4 times.
	endmenu
endef

PKG_CONFIG_DEPENDS:= \
	CONFIG_EINAT_EBPF_IPV6

RUST_PKG_FEATURES:=$(subst $(space),$(comma),$(strip \
	$(if $(CONFIG_EINAT_EBPF_IPV6),ipv6) \
))

define Package/$(PKG_NAME)/conffiles
/etc/config/einat
endef

TARGET_LDFLAGS += -Wl,-rpath-link=$(STAGING_DIR)/usr/lib

define Build/Compile
  cd $(PKG_BUILD_DIR) && \
  $(CARGO_PKG_CONFIG_VARS) \
  $(CARGO) $(CARGO_PKG_CONFIG_ARGS)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/target/$(RUSTUP_TARGET_ARCH)/release/einat $(1)/usr/bin/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
