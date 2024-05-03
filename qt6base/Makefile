include $(TOPDIR)/rules.mk

PKG_NAME:=qt6base
PKG_VERSION:=6.7.0
PKG_RELEASE:=1

PKG_SOURCE:=qtbase-everywhere-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/6.7/$(PKG_VERSION)/submodules
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PKG_BUILD_DIR:=$(BUILD_DIR)/qtbase-everywhere-src-$(PKG_VERSION)

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/qt6base/Default
  SECTION:=libs
  CATEGORY:=Libraries
  SUBMENU:=QT6
  TITLE:=QT6base
  URL:=http://qt-project.org
  #DEPENDS:=+librt +zlib +libgcc +libstdcpp +libpcre2-16 +glib2 +libpthread  +libpng +libjpeg-turbo +libfreetype +mtdev +libinput +libevdev +libudev-zero +libdbus +libiconv-full +giflib +fontconfig +libdrm +krb5-libs +libatomic +libopenssl +libdouble-conversion +libsqlite3 @!LINUX_2_6
endef

define Package/qt6base-core
  $(call Package/qt6base/Default)
  TITLE:=core
endef

define Package/qt6base-concurrent
  $(call Package/qt6base/Default)
  TITLE:=concurrent
  DEPENDS:=+qt6base-core
endef

define Package/qt6base-network
  $(call Package/qt6base/Default)
  TITLE:=network
  DEPENDS:=+qt6base-core
endef

define Package/qt6base-sql
  $(call Package/qt6base/Default)
  TITLE:=sql
  DEPENDS:=+qt6base-core
endef

define Package/qt6base-xml
  $(call Package/qt6base/Default)
  TITLE:=xml
  DEPENDS:=+qt6base-core
endef

define Package/qt6base-serialport
  $(call Package/qt6base/Default)
  TITLE:=serialport
  DEPENDS:=+qt6base-core
endef

define Package/qt6base-serialbus
  $(call Package/qt6base/Default)
  TITLE:=serialbus
  DEPENDS:=+qt6base-core +qt6base-network +qt6base-serialport
endef

define Package/qt6base-xmlpatterns
  $(call Package/qt6base/Default)
  TITLE:=xmlpatterns
  DEPENDS:=+qt6base-core +qt6base-network
endef

define Package/qt6base-test
  $(call Package/qt6base/Default)
  TITLE:=test
  DEPENDS:=+qt6base-core
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
	-dbus-linked \
	-no-directfb \
	-no-dtls\
	-no-egl \
	-no-eglfs \
	-fontconfig \
	-system-freetype \
	-no-gbm \
	-glib \
	-no-gtk \
	-gui \
	-no-harfbuzz \
	-iconv \
	-no-icu \
	-no-kms \
	-gif \
	-ico \
	-system-libjpeg \
	-no-libmd4c \
	-system-libpng \
	-libudev \
	-evdev \
	-libinput \
	-mtdev \
	-no-opengl \
	-no-opengles3 \
	-no-openvg \
	-no-pch \
	-no-slog2 \
	-system-sqlite \
	-no-trace \
	-no-tslib \
	-no-vulkan \
	-widgets \
	-no-xcb \
	-no-xkbcommon \
	-no-zstd \
	-make libs \
	-nomake examples \
	-nomake tests \
	-nomake tools \
	-v

define Package/qt6base-core/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Core.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Core.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Core.la $(1)/usr/lib/
endef

define Package/qt6base-concurrent/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Concurrent.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Concurrent.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Concurrent.la $(1)/usr/lib/
endef

define Package/qt6base-network/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Network.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Network.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Network.la $(1)/usr/lib/
endef

define Package/qt6base-sql/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/Qt/plugins/sqldrivers/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Sql.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Sql.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Sql.la 	$(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/plugins/sqldrivers/*.so $(1)/usr/lib/Qt/plugins/sqldrivers/
endef

define Package/qt6base-xml/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Xml.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Xml.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Xml.la 	$(1)/usr/lib/
endef

define Package/qt6base-serialport/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt6SerialPort.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt6SerialPort.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt6SerialPort.la $(1)/usr/lib/
endef

define Package/qt6base-serialbus/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt6SerialBus.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt6SerialBus.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt6SerialBus.la $(1)/usr/lib/
endef

define Package/qt6base-xmlpatterns/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt6XmlPatterns.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt6XmlPatterns.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt6XmlPatterns.la $(1)/usr/lib/
endef

define Package/qt6base-test/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Test.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Test.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt6Test.la $(1)/usr/lib/
endef

#$(eval $(call BuildPackage,qt6base))
$(eval $(call BuildPackage,qt6base-core))
$(eval $(call BuildPackage,qt6base-concurrent))
$(eval $(call BuildPackage,qt6base-network))
$(eval $(call BuildPackage,qt6base-sql))
$(eval $(call BuildPackage,qt6base-xml))
$(eval $(call BuildPackage,qt6base-serialport))
$(eval $(call BuildPackage,qt6base-serialbus))
$(eval $(call BuildPackage,qt6base-xmlpatterns))
$(eval $(call BuildPackage,qt6base-test))
