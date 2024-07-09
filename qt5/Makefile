include $(TOPDIR)/rules.mk

PKG_NAME:=qt5
PKG_VERSION:=5.15.14
PKG_RELEASE:=1

PKG_SOURCE:=qt-everywhere-opensource-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/5.15/5.15.14/single/
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PKG_BUILD_DIR=$(BUILD_DIR)/qt-everywhere-src-$(PKG_VERSION)

PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0
PKG_CPE_ID:=cpe:/a:qt:qt

include $(INCLUDE_DIR)/package.mk

define Package/qtbase
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+libatomic +libstdcpp +libpcre2-16 +libdbus +libfreetype +libopenssl +libdouble-conversion +libsqlite3 +zlib
endef

define Package/qtbase/description
	qtbase
endef

define Package/qtcharts
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtcharts/description
	qtcharts
endef

define Package/qtgamepad
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtgamepad/description
	qtgamepad
endef

define Package/qttranslations
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qttranslations/description
	qttranslations
endef

define Package/qttools
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qttools/description
	qttools
endef

define Package/qtmultimedia
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtmultimedia/description
	qtmultimedia
endef

define Package/qtnetworkauth
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtnetworkauth/description
	qtnetworkauth
endef

define Package/qtconnectivity
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtconnectivity/description
	qtconnectivity
endef

define Package/qtpurchasing
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtpurchasing/description
	qtpurchasing
endef

define Package/qtlocation
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtlocation/description
	qtlocation
endef

define Package/qtremoteobjects
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtremoteobjects/description
	qtremoteobjects
endef

define Package/qtserialport
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtserialport/description
	qtserialport
endef

define Package/qtserialbus
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase +qtserialport
endef

define Package/qtserialbus/description
	qtserialbus
endef

define Package/qtsensors
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtsensors/description
	qtsensors
endef

define Package/qtsvg
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtsvg/description
	qtsvg
endef

define Package/qtscript
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtscript/description
	qtscript
endef

define Package/qtspeech
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtspeech/description
	qtspeech
endef

define Package/qtwebsockets
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtwebsockets/description
	qtwebsockets
endef

define Package/qtwebchannel
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtwebchannel/description
	qtwebchannel
endef

define Package/qtxmlpatterns
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+qtbase
endef

define Package/qtxmlpatterns/description
	qtxmlpatterns
endef

EXTRA_CFLAGS += $(FPIC) -ffunction-sections -fdata-sections -flto
EXTRA_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS = \
	-sysroot $(STAGING_DIR) \
	-hostprefix $(STAGING_DIR_HOSTPKG) \
	-extprefix $(PKG_INSTALL_DIR)/usr \
	-prefix /usr \
	-bindir /usr/bin \
	-headerdir /usr/include/qt5 \
	-libdir /usr/lib \
	-archdatadir /usr/lib/qt5 \
	-plugindir /usr/lib/qt5/plugins \
	-libexecdir /usr/lib/qt5/libexec \
	-importdir /usr/lib/qt5/imports \
	-qmldir /usr/lib/qt5/qml \
	-datadir /usr/share/qt5 \
	-docdir /usr/share/doc/qt5 \
	-translationdir /usr/share/qt5/translations \
	-sysconfdir /etc/xdg \
	-examplesdir /usr/share/doc/qt5/examples \
	-testsdir /usr/share/doc/qt5/tests \
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
	-system-freetype \
	-no-gbm \
	-no-glib \
	-no-gtk \
	-gui \
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
	-system-sqlite \
	-no-trace \
	-no-tslib \
	-no-vulkan \
	-widgets \
	-no-xcb \
	-no-xkbcommon \
	-no-zstd \
	-make libs \
	-nomake tests \
	-nomake tools \
	-skip qtdeclarative \
	-v


define Build/Compile
	$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR)/$(MAKE_PATH)
endef

define Build/InstallDev
	$(MAKE) -C $(PKG_BUILD_DIR) install
endef

define Package/qtbase/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Core.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Core.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Core.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Concurrent.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Concurrent.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Concurrent.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5DBus.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5DBus.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5DBus.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Gui.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Gui.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Gui.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Network.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Network.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Network.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5PrintSupport.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5PrintSupport.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5PrintSupport.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Sql.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Sql.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Sql.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Test.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Test.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Test.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Widgets.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Widgets.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Widgets.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Xml.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Xml.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Xml.la $(1)/usr/lib/
endef

define Package/qtconnectivity/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Bluetooth.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Bluetooth.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Bluetooth.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Nfc.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Nfc.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Nfc.la $(1)/usr/lib/
endef

define Package/qtcharts/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Charts.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Charts.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Charts.la $(1)/usr/lib/
endef

define Package/qtgamepad/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Gamepad.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Gamepad.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Gamepad.la $(1)/usr/lib/
endef

define Package/qttranslations/install
	$(INSTALL_DIR) $(1)/usr/share/qt/translations/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/qt/translations/*.qm $(1)/usr/share/qt/translations/
endef

define Package/qttools/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Help.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Help.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Help.la $(1)/usr/lib/
endef

define Package/qtmultimedia/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Multimedia.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Multimedia.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Multimedia.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5MultimediaWidgets.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5MultimediaWidgets.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5MultimediaWidgets.la $(1)/usr/lib/
endef

define Package/qtnetworkauth/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5NetworkAuth.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5NetworkAuth.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5NetworkAuth.la $(1)/usr/lib/
endef

define Package/qtpurchasing/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Purchasing.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Purchasing.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Purchasing.la $(1)/usr/lib/
endef

define Package/qtlocation/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Positioning.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Positioning.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Positioning.la $(1)/usr/lib/
endef

define Package/qtremoteobjects/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5RemoteObjects.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5RemoteObjects.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5RemoteObjects.la $(1)/usr/lib/
endef

define Package/qtserialport/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5SerialPort.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5SerialPort.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5SerialPort.la $(1)/usr/lib/
endef

define Package/qtserialbus/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5SerialBus.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5SerialBus.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5SerialBus.la $(1)/usr/lib/
endef

define Package/qtsensors/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Sensors.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Sensors.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Sensors.la $(1)/usr/lib/
endef

define Package/qtsvg/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Svg.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Svg.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Svg.la $(1)/usr/lib/
endef

define Package/qtscript/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Script.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Script.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5Script.la $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5ScriptTools.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5ScriptTools.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5ScriptTools.la $(1)/usr/lib/
endef

define Package/qtspeech/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5TextToSpeech.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5TextToSpeech.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5TextToSpeech.la $(1)/usr/lib/
endef

define Package/qtwebsockets/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5WebSockets.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5WebSockets.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5WebSockets.la $(1)/usr/lib/
endef

define Package/qtwebchannel/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5WebChannel.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5WebChannel.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5WebChannel.la $(1)/usr/lib/
endef

define Package/qtxmlpatterns/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5XmlPatterns.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5XmlPatterns.prl $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libQt5XmlPatterns.la $(1)/usr/lib/
endef

$(eval $(call BuildPackage,qtbase))
$(eval $(call BuildPackage,qtcharts))
$(eval $(call BuildPackage,qtgamepad))
$(eval $(call BuildPackage,qttranslations))
$(eval $(call BuildPackage,qttools))
$(eval $(call BuildPackage,qtmultimedia))
$(eval $(call BuildPackage,qtnetworkauth))
$(eval $(call BuildPackage,qtconnectivity))
$(eval $(call BuildPackage,qtpurchasing))
$(eval $(call BuildPackage,qtlocation))
$(eval $(call BuildPackage,qtremoteobjects))
$(eval $(call BuildPackage,qtserialport))
$(eval $(call BuildPackage,qtserialbus))
$(eval $(call BuildPackage,qtsensors))
$(eval $(call BuildPackage,qtsvg))
$(eval $(call BuildPackage,qtscript))
$(eval $(call BuildPackage,qtspeech))
$(eval $(call BuildPackage,qtwebsockets))
$(eval $(call BuildPackage,qtwebchannel))
$(eval $(call BuildPackage,qtxmlpatterns))
