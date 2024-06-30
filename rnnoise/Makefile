include $(TOPDIR)/rules.mk

PKG_NAME:=rnnoise
PKG_VERSION:=0.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/xiph/rnnoise/releases/download/v$(PKG_VERSION)
PKG_HASH:=90fce4b00b9ff24c08dbfe31b82ffd43bae383d85c5535676d28b0a2b11c0d37

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause license
PKG_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/librnnoise
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Recurrent neural network for audio noise reduction
	URL:=https://github.com/xiph/rnnoise
endef

define Package/librnnoise/description
	RNNoise is a noise suppression library based on a recurrent neural network.
endef

CONFIGURE_ARGS += \
	--prefix=/usr \
	--disable-examples \
	--disable-doc

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include $(1)/usr/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librnnoise.so.* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/rnnoise.pc $(1)/usr/lib/pkgconfig/
endef

define Package/librnnoise/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librnnoise.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,librnnoise))
