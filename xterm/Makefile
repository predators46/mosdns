include $(TOPDIR)/rules.mk

PKG_NAME:=xterm
PKG_VERSION:=390
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=https://invisible-island.net/archives/xterm
PKG_HASH:=75117c3cc5174a09c425ef106e69404d72f5ef05e03a5da00aaf15792d6f9c0f

PKG_INSTALL:=1

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

define Package/xterm
	SECTION:=xorg
	CATEGORY:=Xorg
	SUBMENU:=Terminal
	TITLE:=X Terminal Emulator
	DEPENDS:=+fontconfig +libfreetype +libice +libncurses +terminfo +libx11 +libxaw +libxext +libxft +libxmu +libxpm +libxt
	URL:=https://invisible-island.net/xterm/
endef

define Package/xterm/description
	The xterm program is a terminal emulator for the X Window System.
	It was originally developed in the mid-1980s to provide DEC VT102 and Tektronix 4014 compatible terminals for programs that cannot use the window system directly.
endef

define Package/xterm/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/koi8rxterm $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/resize $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/uxterm $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/xterm $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/X11 $(1)/usr/share/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/applications $(1)/usr/share/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/pixmaps $(1)/usr/share/
endef

$(eval $(call BuildPackage,xterm))
