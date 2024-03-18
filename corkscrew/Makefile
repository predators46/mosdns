include $(TOPDIR)/rules.mk

PKG_NAME:=corkscrew
PKG_VERSION:=2.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/bryanpkc/corkscrew/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=09d70daaa3145070a1e463dbab6ae1cbc62449b1e09c94e158f6017e7c79c9f6

PKG_MAINTAINER:=Andy Syam <privasisource@gmail.com>
PKG_LICENSE:=GPL-2.0 license
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

define Package/corkscrew
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Tunneling SSH through HTTP proxies.
  URL:=https://github.com/bryanpkc/corkscrew
endef

define Package/corkscrew/description
  Corkscrew is a tool for tunneling SSH through HTTP proxies.
endef

define Build/Configure
  $(call Build/Configure/Default,)
endef

define Package/corkscrew/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/corkscrew $(1)/usr/bin/
endef

$(eval $(call BuildPackage,corkscrew))
