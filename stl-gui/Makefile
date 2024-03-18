include $(TOPDIR)/rules.mk

PKG_NAME:=stl-gui
PKG_VERSION:=1.1
PKG_RELEASE:=1

PKG_LICENSE:=GPL-3.0 license
PKG_MAINTAINER:=Andy Syam <privasisource@gmail.com>

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/stl-gui
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Tunnel Ssh Python Gui
  DEPENDS:=+php7 +php7-cgi +php7-mod-session +php7-mod-json +bash +kmod-tun +openvpn-openssl +ip-full +openssh-client +stunnel +lsof +httping +fping +screen +python3 +coreutils-nohup +sshpass +badvpn +corkscrew
endef

define Package/stl-gui/description
 Tunnel Ssh Python Gui
endef

define Build/Compile
endef

define Package/stl-gui/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/bin/* $(1)/usr/bin/
	mkdir -p $(1)/root/akun
	#mkdir -p $(1)/root/.ssh
	$(INSTALL_DIR) $(1)/root/akun
	$(INSTALL_BIN) ./files/*.py $(1)/root/akun/
	$(CP) ./files/akun/* $(1)/root/akun/
	$(INSTALL_DIR) $(1)/www
	$(CP) ./files/stl $(1)/www/
endef

$(eval $(call BuildPackage,stl-gui))
