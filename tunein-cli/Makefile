include $(TOPDIR)/rules.mk

PKG_NAME:=tunein-cli
PKG_VERSION:=0.2.6
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/tsirysndr/tunein-cli/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=skip

PKG_MAINTAINER:=
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host protobuf/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/xorg/rust/rust-package.mk

define Package/tunein-cli
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=Browse and listen to thousands of radio stations across the globe right from your terminal
  DEPENDS:=$(RUST_ARCH_DEPENDS) +alsa-lib +libopenssl +protobuf
  URL:=https://github.com/tsirysndr/tunein-cli
endef

define Package/tunein-cli/description
  A command line interface for TuneIn Radio. You can search for stations, play them, and see what's currently playing.
endef

$(eval $(call RustBinPackage,tunein-cli))
$(eval $(call BuildPackage,tunein-cli))
