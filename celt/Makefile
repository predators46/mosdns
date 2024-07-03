#
# Copyright (C) 2008-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=celt
PKG_VERSION:=0.11.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://ftp.osuosl.org/pub/xiph/releases/celt/
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/celt
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=CELT is a very low delay audio codec designed for high-quality communications.
  URL:=https://ftp.osuosl.org/pub/xiph/releases/celt/
  DEPENDS:=+libogg
endef

define Package/celt/description
Traditional full-bandwidth  codecs such as Vorbis and AAC can offer high quality but they require codec delays of hundreds of milliseconds,
which makes them unsuitable for real-time interactive applications like tele-conferencing.
Speech targeted codecs, such as Speex or G.722, have lower 20-40ms delays but their speech focus and limited sampling rates restricts their quality, especially for music.
endef

TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS += \
	--disable-oggtest \
	--enable-custom-modes \
	--enable-float-approx \
	--with-ogg-libraries="$(STAGING_DIR)/usr/lib" \
	--with-ogg-includes="$(STAGING_DIR)/usr/include"

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/celt/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/celt/* $(1)/usr/include/celt/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.{so*,a,la} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig/
endef

define Package/celt/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/{celtdec,celtenc} $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcelt0.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,celt))
