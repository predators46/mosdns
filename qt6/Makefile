include $(TOPDIR)/rules.mk

PKG_NAME:=qt6
PKG_BASE_VERSION:=6.6
PKG_SUBVERSION:=3
PKG_VERSION:=$(PKG_BASE_VERSION).$(PKG_SUBVERSION)
PKG_RELEASE:=1

PKG_SOURCE:=qt-everywhere-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/$(PKG_BASE_VERSION)/$(PKG_VERSION)/single
PKG_HASH:=skip

HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/qt-everywhere-src-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/qt-everywhere-src-$(PKG_VERSION)

PKG_MAINTAINER:=
PKG_LICENSE:=LGPL-2.1
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=qt6/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

CMAKE_INSTALL:=1

STRIP:=$(TARGET_CROSS)strip $(call qstrip,$(CONFIG_STRIP_ARGS))

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/qt6
  SECTION:=libs
  CATEGORY:=Libraries
  SUBMENU:=Qt6
  TITLE:=Qt6
  URL:=http://qt-project.org
  DEPENDS:=+libatomic +libstdcpp +zlib +libpcre2 +libfreetype
endef

define Package/badvpn/description
  Qt is a full development framework with tools designed to streamline the creation of applications and user interfaces for desktop, embedded, and mobile platforms.
endef

CMAKE_HOST_OPTIONS += \
	-DBUILD_SHARED_LIBS=OFF \
	-DFEATURE_optimize_full=ON \
	-DFEATURE_zstd=OFF \
	-DFEATURE_dbus=ON \
	-DFEATURE_gui=ON \
        -DINPUT_opengl=no \
	-DFEATURE_network=ON \
	-DFEATURE_openssl=OFF \
	-DFEATURE_sql=OFF \
	-DFEATURE_testlib=OFF \
	-DFEATURE_xml=ON

CMAKE_OPTIONS += \
	-DINSTALL_PLUGINSDIR=/usr/lib/qt6plugins \
	-DCMAKE_SYSROOT=$(STAGING_DIR) \
	-DQT_HOST_PATH=$(STAGING_DIR_HOSTPKG) \
	-DQT_QMAKE_TARGET_MKSPEC=devices/linux-openwrt-g++ \
	-DQT_BUILD_EXAMPLES=OFF \
	-DQT_BUILD_TESTS=OFF \
	-DQT_BUILD_TOOLS_WHEN_CROSSCOMPILING=OFF \
	-DBUILD_SHARED_LIBS=ON \
	-DFEATURE_optimize_full=ON \
	-DFEATURE_system_zlib=ON \
	-DFEATURE_zstd=OFF \
	-DFEATURE_backtrace=OFF \
	-DFEATURE_system_doubleconversion=OFF \
	-DFEATURE_glib=OFF \
	-DFEATURE_icu=OFF \
	-DFEATURE_mimetype_database=ON \
	-DFEATURE_system_pcre2=ON \
	-DFEATURE_concurrent=$(if $(CONFIG_PACKAGE_libQt6Concurrent),ON,OFF) \
	-DFEATURE_dbus=$(if $(CONFIG_PACKAGE_libQt6DBus),ON,OFF) \
	-DFEATURE_gui=$(if $(CONFIG_PACKAGE_libQt6Gui),ON,OFF) \
	-DINPUT_opengl=no \
	-DFEATURE_system_freetype=ON \
	-DFEATURE_accessibility=OFF \
	-DFEATURE_harfbuzz=OFF \
	-DFEATURE_gif=OFF \
	-DFEATURE_ico=OFF \
	-DFEATURE_jpeg=OFF \
	-DFEATURE_png=OFF \
	-DFEATURE_texthtmlparser=OFF \
	-DFEATURE_cssparser=OFF \
	-DFEATURE_textodfwriter=OFF \
	-DFEATURE_textmarkdownreader=OFF \
	-DFEATURE_textmarkdownwriter=OFF \
	-DFEATURE_sessionmanager=OFF \
	-DFEATURE_evdev=OFF \
	-DFEATURE_vnc=OFF \
	-DFEATURE_linuxfb=OFF \
	-DFEATURE_network=$(if $(CONFIG_PACKAGE_libQt6Network),ON,OFF) \
	-DFEATURE_openssl=OFF \
	-DFEATURE_openssl_linked=ON \
	-DFEATURE_openssl_runtime=OFF \
	-DFEATURE_ocsp=OFF \
	-DFEATURE_printsupport=$(if $(CONFIG_PACKAGE_libQt6PrintSupport),ON,OFF) \
	-DFEATURE_sql=$(if $(CONFIG_PACKAGE_libQt6Sql),ON,OFF) \
	-DFEATURE_sqlmodel=OFF \
	-DFEATURE_sql_sqlite=ON \
	-DFEATURE_system_sqlite=OFF \
	-DFEATURE_sql_db2=OFF \
	-DFEATURE_sql_ibase=OFF \
	-DFEATURE_sql_mysql=OFF \
	-DFEATURE_sql_oci=OFF \
	-DFEATURE_sql_odbc=OFF \
	-DFEATURE_sql_psql=OFF \
	-DFEATURE_testlib=$(if $(CONFIG_PACKAGE_libQt6Test),ON,OFF) \
	-DFEATURE_itemmodeltester=OFF \
	-DFEATURE_widgets=$(if $(CONFIG_PACKAGE_libQt6Widgets),ON,OFF) \
	-DFEATURE_xml=$(if $(CONFIG_PACKAGE_libQt6Xml),ON,OFF) \
	-DFEATURE_tuiotouch=$(if $(CONFIG_PACKAGE_qt6-plugin-libqtuiotouchplugin),ON,OFF)

define Package/qt6/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tun2socks/badvpn-tun2socks $(1)/usr/bin/badvpn-tun2socks
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/udpgw/badvpn-udpgw $(1)/usr/bin/badvpn-udpgw
endef

$(eval $(call BuildPackage,qt6))
$(eval $(call HostBuild))
