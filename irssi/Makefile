#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=irssi
PKG_VERSION:=1.4.5
PKG_RELEASE:=4

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://github.com/irssi/irssi/releases/download/$(PKG_VERSION)/
PKG_HASH:=72a951cb0ad622785a8962801f005a3a412736c7e7e3ce152f176287c52fe062

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_CPE_ID:=cpe:/a:irssi:irssi

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include $(TOPDIR)/feeds/packages/lang/perl/perlver.mk

define Package/irssi
  SUBMENU:=Instant Messaging
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+glib2 +libncurses +libpthread +libopenssl +perl +perlbase-essential +perlbase-dynaloader
  TITLE:=Console IRC client
  MAINTAINER:=Peter Wagner <tripolar@gmx.at>
  URL:=https://irssi.org/
endef

define Package/irssi/description
	Irssi is a terminal based IRC client for UNIX systems.
endef

TARGET_LDFLAGS += -Wl,--gc-sections

PERL_SITELIB:=/usr/lib/perl$(PERL_MAJOR)/$(PERL_VERSION2)
PERL_USE_LIB:="$(PERL_SITELIB)"

CONFIGURE_VARS += \
	ac_cv_path_perlpath="$(STAGING_DIR_HOSTPKG)/usr/bin/perl$(PERL_VERSION)" \
	PERL_USE_LIB="$(PERL_SITELIB)"
	PERL_CFLAGS="-D_LARGEFILE_SOURCE $(if $(CONFIG_USE_MUSL),-D_LARGEFILE64_SOURCE) -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_GNU_SOURCE -I$(STAGING_DIR)$(PERL_SITELIB)/CORE" \
	PERL_INC="-I$(STAGING_DIR)$(PERL_SITELIB)/CORE" \
	PERL_LDFLAGS="-Wl,-rpath,$(PERL_SITELIB)/CORE -L$(STAGING_DIR)$(PERL_SITELIB)/CORE -lperl" \
	PERL_LIBDIR="-L$(PERL_SITELIB)/CORE" \
	PERL_LIBS="$(EXTRA_LIBDIRS:%=-L%) $(EXTRA_LIBS:%=-l%)" \
	PERL_SITEDIR="$(PERL_SITELIB)"

CONFIGURE_ARGS += \
	--prefix=/usr \
	--disable-static \
	--enable-shared \
	--with-perl-lib="$(PERL_SITELIB)" \
	--with-perl=yes

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/irssi
	$(CP) $(PKG_INSTALL_DIR)/usr/include/irssi/* $(1)/usr/include/irssi/
endef

define Package/irssi/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/irssi $(1)/usr/bin/
	#$(INSTALL_DIR) $(1)/usr/lib/irssi/modules
	#$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/irssi/modules/{libfe_perl.so,libperl_core.so} $(1)/usr/lib/irssi/modules/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/irssi $(1)/usr/share/
	$(INSTALL_DIR) $(1)$(PERL_SITELIB)
	$(CP) $(PKG_INSTALL_DIR)$(PERL_SITELIB)/{Irssi,Irssi.pm} $(1)$(PERL_SITELIB)
	$(INSTALL_DIR) $(1)$(PERL_SITELIB)/auto/Irssi/UI
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)$(PERL_SITELIB)/auto/Irssi/UI/UI.so $(1)$(PERL_SITELIB)/auto/Irssi/UI/
	$(INSTALL_DIR) $(1)$(PERL_SITELIB)/auto/Irssi
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)$(PERL_SITELIB)/auto/Irssi/Irssi.so $(1)$(PERL_SITELIB)/auto/Irssi/
	$(INSTALL_DIR) $(1)$(PERL_SITELIB)/auto/Irssi/TextUI
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)$(PERL_SITELIB)/auto/Irssi/TextUI/TextUI.so $(1)$(PERL_SITELIB)/auto/Irssi/TextUI/
	$(INSTALL_DIR) $(1)$(PERL_SITELIB)/auto/Irssi/Irc
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)$(PERL_SITELIB)/auto/Irssi/Irc/Irc.so $(1)$(PERL_SITELIB)/auto/Irssi/Irc/
endef

$(eval $(call BuildPackage,irssi))
