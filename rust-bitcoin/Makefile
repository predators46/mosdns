include $(TOPDIR)/rules.mk

PKG_NAME:=rust-bitcoin
PKG_VERSION:=0.31.1
PKG_RELEASE:=1

PKG_SOURCE:=bitcoin-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/rust-bitcoin/rust-bitcoin/archive/
PKG_HASH:=544be22147a9e85b94f48e191c386ce53a7dac43291f9782480f5a6b0a9eed40

PKG_MAINTAINER:=
PKG_LICENSE:=CC0-1.0 license
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/rust-bitcoin-bitcoin-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=rustup/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/mosdns/rustup/rust-values.mk

define Package/rust-bitcoin
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Rust Bitcoin library
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  URL:=https://github.com/rust-bitcoin/rust-bitcoin
endef

define Package/rust-bitcoin/description
  Library with support for de/serialization, parsing and executing on data-structures and network messages related to Bitcoin.
endef

define Build/Compile
  cd $(PKG_BUILD_DIR) && \
  $(CARGO_PKG_CONFIG_VARS) \
  $(CARGO) $(CARGO_PKG_CONFIG_ARGS)
endef

define Package/rust-bitcoin/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/target/$(RUSTUP_TARGET_ARCH)/release/* $(1)/usr/bin/
endef

$(eval $(call BuildPackage,rust-bitcoin))
