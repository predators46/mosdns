include $(TOPDIR)/rules.mk

PKG_NAME:=librespot
PKG_VERSION:=0.4.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/librespot-org/librespot/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=cc8cb81bdbaa5abf366170dec5e6b8c0ecf570a7cb68f04483e9f7eed338ca61

PKG_MAINTAINER:=Andy Syam <privasisource@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/mosdns/rust/rust-package.mk

define Package/librespot
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=Open Source Spotify client library
  DEPENDS:=$(RUST_ARCH_DEPENDS) +alsa-lib
  URL:=https://github.com/librespot-org/librespot
endef

define Package/librespot/description
  librespot is an open source client library for Spotify.
  It enables applications to use Spotify service to control and play music via various backends, and to act as a Spotify Connect receiver.
  It is an alternative to the official and now deprecated closed-source libspotify.
  Additionally, it will provide extra features which are not available in the official library.
endef

$(eval $(call RustBinPackage,librespot))
$(eval $(call BuildPackage,librespot))
