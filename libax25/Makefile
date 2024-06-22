include $(TOPDIR)/rules.mk

PKG_NAME:=libax25
PKG_VERSION:=1.2.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/ve7fet/linuxax25/archive/refs/tags/
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=LGPL-2.1-or-later
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DIR:=$(BUILD_DIR)/linuxax25-libax25-$(PKG_VERSION)
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libax25
	SECTION:=net
	CATEGORY:=Network
	TITLE:=set of functions making it easier to write hamradio programs
	DEPENDS:=+libstdcpp +zlib
	URL:=https://github.com/ve7fet/linuxax25
endef

define Package/libax25/description
	set of functions making it easier to write hamradio programs
endef

define Build/Configure
	(cd $(PKG_BUILD_DIR)/libax25; ./autogen.sh );
	$(call Build/Configure/Default)
endef

define Build/Compile
	$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR)/libax25
endef

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/{netax25,netrom,netrose} \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

define Package/libax25/install
	$(INSTALL_DIR) \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libax25))
