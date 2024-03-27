include $(TOPDIR)/rules.mk

PKG_NAME:=shadow-tls
PKG_VERSION:=0.2.25
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/ihciah/shadow-tls/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=1d1d436734823ba0302de6e91883ed892ea710769c722a139990194ff5837224

PKG_MAINTAINER:=example <example@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rustup/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/mosdns/rustup/rust-values.mk

define Package/shadow-tls
  SECTION:=net
  CATEGORY:=Network
  TITLE:=A proxy to expose real tls handshake to the firewall.
  DEPENDS:=@USE_MUSL @(aarch64||arm||x86_64) @!(TARGET_x86_geode||TARGET_x86_legacy)
  URL:=https://github.com/ihciah/shadow-tls
endef

define Package/shadow-tls/description
  It works like trojan but it does not require signing certificate.
  The firewall will see real tls handshake with valid certificate that you choose.
endef

define Build/Compile
  cd $(PKG_BUILD_DIR) && \
  $(CARGO_PKG_CONFIG_VARS) \
  $(CARGO) $(CARGO_PKG_CONFIG_ARGS)
endef

define Package/shadow-tls/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/target/$(RUSTUP_TARGET_ARCH)/release/shadow-tls $(1)/usr/bin/
endef

$(eval $(call BuildPackage,shadow-tls))
