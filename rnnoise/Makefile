#
# Copyright (C) 2006-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rnnoise
PKG_VERSION:=0.4.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/xiph/rnnoise
PKG_SOURCE_VERSION:=6cbfd53eb348a8d394e0757b4025c6ded34eb2b6
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=
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

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include $(1)/usr/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librnnoise.{a,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/rnnoise.pc $(1)/usr/lib/pkgconfig/
endef

define Package/librnnoise/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librnnoise.so.* $(1)/usr/lib/
endef

TARGET_CFLAGS += $(FPIC)

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static \
	--disable-examples \
	--disable-doc

$(eval $(call BuildPackage,librnnoise))
