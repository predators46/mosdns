#
# Copyright (C) 2006-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/uclibc++.mk

PKG_NAME:=mysql
PKG_VERSION:=5.1.73
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://downloads.mysql.com/archives/get/p/23/file/
PKG_HASH:=skip

PKG_MAINTAINER:=Jo-Philipp Wich <jo@mein.io>
PKG_LICENSE:=GPL-2.0

PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

#PKG_FIXUP:=libtool
#PKG_REMOVE_FILES:=aclocal.m4

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libmysqlclient/Default
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=$(CXX_DEPENDS) +zlib
  TITLE:=MySQL client library
  URL:=http://dev.mysql.com/
endef

define Package/mysql-server
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libmysqlclient +libpthread +libncurses +libreadline
  TITLE:=MySQL Server
  URL:=http://dev.mysql.com/
  SUBMENU:=database
endef

define Package/libmysqlclient
  $(call Package/libmysqlclient/Default)
endef

define Package/libmysqlclient-r
  $(call Package/libmysqlclient/Default)
  TITLE += threadsafe
  DEPENDS+= +libpthread
endef

ifneq ($(CONFIG_USE_UCLIBCXX),)
  TARGET_CXX=g++-uc
endif

TARGET_CFLAGS += $(FPIC)

CMAKE_OPTIONS +=
	-Wno-dev


define Build/InstallDev
	$(INSTALL_DIR) $(2)/bin $(1)/usr/bin $(1)/usr/include $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mysql_config $(1)/usr/bin/
	ln -sf $(STAGING_DIR)/usr/bin/mysql_config $(2)/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/mysql $(1)/usr/include/
	# NOTE: needed for MySQL-Python
	$(CP) $(PKG_BUILD_DIR)/include/mysqld_error.h $(1)/usr/include/mysql/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/mysql $(1)/usr/lib/
	rm -f $(1)/usr/lib/mysql/libmysqlclient.la
endef

define Package/libmysqlclient/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/mysql/libmysqlclient.so.* $(1)/usr/lib/
endef

define Package/libmysqlclient-r/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/mysql/libmysqlclient_r.so.* $(1)/usr/lib/
endef

define Package/mysql-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mysql $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/mysqld $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/myisamchk $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mysqladmin $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mysqldump $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mysql_install_db $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/my_print_defaults $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) files/mysqld.init $(1)/etc/init.d/mysqld
	$(INSTALL_CONF) conf/my.cnf $(1)/etc/
	$(INSTALL_DIR) $(1)/usr/share/mysql
	$(INSTALL_DIR) $(1)/usr/share/mysql/english
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/share/mysql/english/errmsg.sys $(1)/usr/share/mysql/english
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/share/mysql/fill_help_tables.sql $(1)/usr/share/mysql/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/share/mysql/mysql_system_tables.sql $(1)/usr/share/mysql/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/share/mysql/mysql_system_tables_data.sql $(1)/usr/share/mysql/
endef

define Package/mysql-server/conffiles
/etc/my.cnf
endef

$(eval $(call BuildPackage,mysql-server))
$(eval $(call BuildPackage,libmysqlclient))
$(eval $(call BuildPackage,libmysqlclient-r))
