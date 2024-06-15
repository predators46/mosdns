include $(TOPDIR)/rules.mk

PKG_NAME:=code-radio-cli
PKG_VERSION:=1.0.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/JasonWei512/code-radio-cli/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=skip

PKG_MAINTAINER:=
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/xorg/rust/rust-package.mk

define Package/code-radio-cli
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=A command line music radio client
  DEPENDS:=$(RUST_ARCH_DEPENDS) +alsa-lib
  URL:=https://github.com/JasonWei512/code-radio-cli
endef

define Package/code-radio-cli/description
  A command line music radio client for https://coderadio.freecodecamp.org (about), written in Rust.
endef

$(eval $(call RustBinPackage,code-radio-cli))
$(eval $(call BuildPackage,code-radio-cli))
