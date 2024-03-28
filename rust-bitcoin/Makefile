include $(TOPDIR)/rules.mk

PKG_NAME:=rust-bitcoin
PKG_VERSION:=0.30.2
PKG_RELEASE:=1

PKG_SOURCE:=bitcoin-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/rust-bitcoin/rust-bitcoin/archive/
PKG_HASH:=2ba5112e809b81a0ffecce82c4f4f1c949af92e2b40f23e49933f56894dd65e0

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
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/target/$(RUSTUP_TARGET_ARCH)/release/rust-bitcoin $(1)/usr/bin/
endef

$(eval $(call BuildPackage,rust-bitcoin))
