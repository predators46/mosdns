include $(TOPDIR)/rules.mk

PKG_NAME:=qt5base
PKG_VERSION:=5.15.13
PKG_RELEASE:=1

PKG_SOURCE:=qtbase-everywhere-opensource-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/5.15/$(PKG_VERSION)/submodules
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PKG_BUILD_DIR=$(BUILD_DIR)/qtbase-everywhere-src-$(PKG_VERSION)

PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk

define Package/qt5base/Default
  SECTION:=libs
  CATEGORY:=Libraries
  SUBMENU:=Qt5
  TITLE:=Qt5base
  URL:=http://qt-project.org
  DEPENDS:=+librt +zlib +libgcc +libstdcpp +libpcre2-16 +glib2 +libpthread +libatomic +libopenssl +libdouble-conversion +libsqlite3 @!LINUX_2_6
endef

define Package/qt5base-core
  $(call Package/qt5base/Default)
  TITLE:=core
endef

define Package/qt5base-concurrent
  $(call Package/qt5base/Default)
  TITLE:=concurrent
  DEPENDS:=+qt5base-core
endef

define Package/qt5base-network
  $(call Package/qt5base/Default)
  TITLE:=network
  DEPENDS:=+qt5base-core
endef

define Package/qt5base-sql
  $(call Package/qt5base/Default)
  TITLE:=sql
  DEPENDS:=+qt5base-core
endef

define Package/qt5base-xml
  $(call Package/qt5base/Default)
  TITLE:=xml
  DEPENDS:=+qt5base-core
endef

define Package/qt5base-serialport
  $(call Package/qt5base/Default)
  TITLE:=serialport
  DEPENDS:=+qt5base-core
endef

define Package/qt5base-serialbus
  $(call Package/qt5base/Default)
  TITLE:=serialbus
  DEPENDS:=+qt5base-core +qt5base-network +qt5base-serialport
endef

define Package/qt5base-xmlpatterns
  $(call Package/qt5base/Default)
  TITLE:=xmlpatterns
  DEPENDS:=+qt5base-core +qt5base-network
endef

define Package/qt5base-test
  $(call Package/qt5base/Default)
  TITLE:=test
  DEPENDS:=+qt5base-core
endef

EXTRA_CFLAGS += $(FPIC) -ffunction-sections -fdata-sections -flto
EXTRA_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS = \
	-sysroot $(STAGING_DIR) \
	-hostprefix $(STAGING_DIR_HOSTPKG) \
	-extprefix $(STAGING_DIR)/usr \
	-prefix /usr \
	-archdatadir /usr/share/Qt \
	-datadir /usr/share/Qt \
	-plugindir /usr/lib/Qt/plugins \
	-device linux-generic-g++ \
	-device-option CROSS_COMPILE="$(TARGET_CROSS)" \
	-device-option COMPILER_FLAGS="$(TARGET_CFLAGS) $(EXTRA_CFLAGS) $(TARGET_CPPFLAGS) $(EXTRA_CPPFLAGS)" \
	-device-option LINKER_FLAGS="$(TARGET_LDFLAGS) $(EXTRA_LDFLAGS)" \
	-confirm-license \
	-opensource \
	-release \
	-shared \
	-strip \
	-no-rpath \
	-no-use-gold-linker \
	-ltcg \
	-mimetype-database \
	-openssl-linked \
	-system-doubleconversion \
	-system-pcre \
	-system-zlib \
	$(if $(findstring i386,$(ARCH)),-no-sse2 -no-sse4.1) \
	-no-angle \
	-no-cups \
	-no-dbus \
	-no-directfb \
	-no-dtls\
	-no-egl \
	-no-eglfs \
	-no-freetype \
	-no-gbm \
	-no-glib \
	-no-gtk \
	-no-gui \
	-no-harfbuzz \
	-no-iconv \
	-no-icu \
	-no-kms \
	-no-libjpeg \
	-no-libmd4c \
	-no-libpng \
	-no-libudev \
	-no-mtdev \
	-no-opengl \
	-no-opengles3 \
	-no-openvg \
	-no-pch \
	-no-slog2 \
	-plugin-sql-sqlite \
	-system-sqlite \
	-no-trace \
	-no-tslib \
	-no-vulkan \
	-no-widgets \
	-no-xcb \
	-no-xkbcommon \
	-no-zstd \
	-no-compile-examples \
	-no-feature-gssapi \
	-no-feature-testlib \
	-make libs \
	-nomake examples \
	-nomake tests \
	-nomake tools \
	-v

define Package/qt5base-core/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Core.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Core.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Core.la $(1)/usr/lib/
endef

define Package/qt5base-concurrent/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Concurrent.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Concurrent.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Concurrent.la $(1)/usr/lib/
endef

define Package/qt5base-network/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Network.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Network.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Network.la $(1)/usr/lib/
endef

define Package/qt5base-sql/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/Qt/plugins/sqldrivers/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Sql.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Sql.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Sql.la 	$(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/plugins/sqldrivers/*.so $(1)/usr/lib/Qt/plugins/sqldrivers/
endef

define Package/qt5base-xml/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Xml.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Xml.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Xml.la 	$(1)/usr/lib/
endef

define Package/qt5base-serialport/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt5SerialPort.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt5SerialPort.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt5SerialPort.la $(1)/usr/lib/
endef

define Package/qt5base-serialbus/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt5SerialBus.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt5SerialBus.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt5SerialBus.la $(1)/usr/lib/
endef

define Package/qt5base-xmlpatterns/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt5XmlPatterns.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt5XmlPatterns.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt5XmlPatterns.la $(1)/usr/lib/
endef

define Package/qt5base-test/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Test.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Test.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Test.la $(1)/usr/lib/
endef

$(eval $(call BuildPackage,qt5base))
$(eval $(call BuildPackage,qt5base-core))
$(eval $(call BuildPackage,qt5base-concurrent))
$(eval $(call BuildPackage,qt5base-network))
$(eval $(call BuildPackage,qt5base-sql))
$(eval $(call BuildPackage,qt5base-xml))
$(eval $(call BuildPackage,qt5base-serialport))
$(eval $(call BuildPackage,qt5base-serialbus))
$(eval $(call BuildPackage,qt5base-xmlpatterns))
$(eval $(call BuildPackage,qt5base-test))
