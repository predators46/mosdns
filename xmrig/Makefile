include $(TOPDIR)/rules.mk

PKG_NAME:=xmrig
PKG_VERSION:=6.21.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/xmrig/xmrig/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=5d76fb19190956c564b405119315bc93db4ed8062b251d5e96bed70c5fa8033c

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=GPL-3.0 license
PKG_LICENSE_FILES:=LICENSE

CMAKE_BINARY_SUBDIR := build
CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/xmrig
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=xmrig (CPU Miner)
	URL:=https://github.com/xmrig/xmrig
	DEPENDS:=+libhwloc +libuv +libpthread +libncurses +jansson +libopenssl +zlib +libstdcpp
endef

define Package/xmrig/description
	Xmrig Cpuminer is a multi-threaded CPU miner for bitcoin and derivative coins.
	Do not use on multiple block chains at the same time!
endef

CMAKE_OPTIONS +=

define Package/xmrig/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(CP) $(CMAKE_BINARY_DIR)/xmrig $(1)/usr/bin/
endef

$(eval $(call BuildPackage,xmrig))
