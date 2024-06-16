include $(TOPDIR)/rules.mk

PKG_NAME:=radio-cli
PKG_VERSION:=2.3.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/margual56/radio-cli/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=2834898b18eb7d80a6d9c601cf1075add8422992191d5388c1b9fecfda8388eb

PKG_MAINTAINER:=
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/xorg/rust/rust-package.mk

define Package/radio-cli
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=A simple radio CLI written in rust.
  DEPENDS:=$(RUST_ARCH_DEPENDS) +libopenssl
  URL:=https://github.com/margual56/radio-cli
endef

define Package/radio-cli/description
  Now it can search for any radio station! Just select the "Other" option to be prompted for the search.
endef

$(eval $(call RustBinPackage,radio-cli))
$(eval $(call BuildPackage,radio-cli))
