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

define Package/qt5/Default
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
endef

define Package/qt5-bluetooth
	$(call Package/qt5/Default)
	TITLE+=bluetooth
	DEPENDS+=+qt5-core
endef

define Package/qt5-charts
	$(call Package/qt5/Default)
	TITLE+=charts
	DEPENDS+=+qt5-core
endef

define Package/qt5-core
	$(call Package/qt5/Default)
	TITLE+=core
	DEPENDS+=+libatomic +libpcre2-16 +zlib
endef

define Package/qt5-concurrent
	$(call Package/qt5/Default)
	TITLE+=concurrent
	DEPENDS+=+qt5-core
endef

define Package/qt5-dbus
	$(call Package/qt5/Default)
	TITLE+=dbus
	DEPENDS+=+qt5-core +libdbus
endef

define Package/qt5-gui
	$(call Package/qt5/Default)
	TITLE+=gui
	DEPENDS+=+qt5-core +qt5-dbus +libfreetype
endef

define Package/qt5-gamepad
	$(call Package/qt5/Default)
	TITLE+=gamepad
	DEPENDS+=+qt5-core
endef

define Package/qt5-help
	$(call Package/qt5/Default)
	TITLE+=help
	DEPENDS+=+qt5-core
endef

define Package/qt5-multimedia
	$(call Package/qt5/Default)
	TITLE+=multimedia
	DEPENDS+=+qt5-core
endef

define Package/qt5-multimediawidgets
	$(call Package/qt5/Default)
	TITLE+=multimedia widgets
	DEPENDS+=+qt5-core
endef

define Package/qt5-network
	$(call Package/qt5/Default)
	TITLE+=network
	DEPENDS+=+qt5-core +libopenssl
endef

define Package/qt5-networkauth
	$(call Package/qt5/Default)
	TITLE+=networkauth
	DEPENDS+=+qt5-core
endef

define Package/qt5-nfc
	$(call Package/qt5/Default)
	TITLE+=nfc
	DEPENDS+=+qt5-core
endef

define Package/qt5-printsupport
	$(call Package/qt5/Default)
	TITLE+=printsupport
	DEPENDS+=+qt5-core +qt5-widgets
endef

define Package/qt5-purchasing
	$(call Package/qt5/Default)
	TITLE+=purchasing
	DEPENDS+=+qt5-core
endef

define Package/qt5-positioning
	$(call Package/qt5/Default)
	TITLE+=positioning
	DEPENDS+=+qt5-core
endef

define Package/qt5-remoteobjects
	$(call Package/qt5/Default)
	TITLE+=remote objects
	DEPENDS+=+qt5-core
endef

define Package/qt5-serialport
	$(call Package/qt5/Default)
	TITLE+=serialport
	DEPENDS+=+qt5-core
endef

define Package/qt5-serialbus
	$(call Package/qt5/Default)
	TITLE+=serialbus
	DEPENDS+=+qt5-core +qt5-network +qt5-serialport
endef

define Package/qt5-sensors
	$(call Package/qt5/Default)
	TITLE+=sensors
	DEPENDS+=+qt5-core
endef

define Package/qt5-sql
	$(call Package/qt5/Default)
	TITLE+=sql
	DEPENDS+=+qt5-core
endef

define Package/qt5-svg
	$(call Package/qt5/Default)
	TITLE+=svg
	DEPENDS+=+qt5-core
endef

define Package/qt5-script
	$(call Package/qt5/Default)
	TITLE+=script
	DEPENDS+=+qt5-core
endef

define Package/qt5-scripttools
	$(call Package/qt5/Default)
	TITLE+=script tools
	DEPENDS+=+qt5-core +qt5-script
endef

define Package/qt5-test
	$(call Package/qt5/Default)
	TITLE+=test
	DEPENDS+=+qt5-core
endef

define Package/qt5-texttospeech
	$(call Package/qt5/Default)
	TITLE+=text to speech
	DEPENDS+=+qt5-core
endef

define Package/qt5-widgets
	$(call Package/qt5/Default)
	TITLE+=widgets
	DEPENDS+=+qt5-core +qt5-gui
endef

define Package/qt5-websockets
	$(call Package/qt5/Default)
	TITLE+=websockets
	DEPENDS+=+qt5-core
endef

define Package/qt5-webchannel
	$(call Package/qt5/Default)
	TITLE+=webchannel
	DEPENDS+=+qt5-core
endef

define Package/qt5-xml
	$(call Package/qt5/Default)
	TITLE+=xml
	DEPENDS+=+qt5-core
endef

define Package/qt5-xmlpatterns
	$(call Package/qt5/Default)
	TITLE+=xml patterns
	DEPENDS+=+qt5-core +qt5-network
endef

EXTRA_CFLAGS += $(FPIC) -ffunction-sections -fdata-sections -flto
EXTRA_LDFLAGS+=-L$(PKG_BUILD_DIR) -L$(STAGING_DIR)/usr/lib -L$(STAGING_DIR)/lib

CONFIGURE_ARGS = \
	-sysroot $(STAGING_DIR) \
	-hostprefix $(STAGING_DIR_HOSTPKG) \
	-extprefix $(STAGING_DIR)/usr \
	-prefix /usr \
	-archdatadir /usr/share/Qt \
	-datadir /usr/share/Qt \
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
	-qt-doubleconversion \
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
	-sql-sqlite \
	-no-trace \
	-no-tslib \
	-no-vulkan \
	-widgets \
	-no-xcb \
	-no-xkbcommon \
	-no-zstd \
	-no-compile-examples \
	-feature-concurrent \
	-no-feature-gssapi \
	-feature-testlib \
	-make libs \
	-nomake examples \
	-nomake tests \
	-nomake tools \
	-skip qtdeclarative \
	-v

define Build/Compile
	$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR)
endef

define Build/InstallDev
	$(MAKE) -C $(PKG_BUILD_DIR) install
endef

define Package/qt5-bluetooth/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtconnectivity/lib/libQt5Bluetooth.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtconnectivity/lib/libQt5Bluetooth.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtconnectivity/lib/libQt5Bluetooth.la $(1)/usr/lib/
endef

define Package/qt5-charts/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtcharts/lib/libQt5Charts.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtcharts/lib/libQt5Charts.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtcharts/lib/libQt5Charts.la $(1)/usr/lib/
endef

define Package/qt5-core/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Core.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Core.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Core.la $(1)/usr/lib/
endef

define Package/qt5-concurrent/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Concurrent.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Concurrent.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Concurrent.la $(1)/usr/lib/
endef

define Package/qt5-dbus/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5DBus.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5DBus.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5DBus.la $(1)/usr/lib/
endef

define Package/qt5-gui/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Gui.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Gui.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Gui.la $(1)/usr/lib/
endef

define Package/qt5-gamepad/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtgamepad/lib/libQt5Gamepad.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtgamepad/lib/libQt5Gamepad.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtgamepad/lib/libQt5Gamepad.la $(1)/usr/lib/
endef

define Package/qt5-help/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qttools/lib/libQt5Help.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qttools/lib/libQt5Help.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qttools/lib/libQt5Help.la $(1)/usr/lib/
endef

define Package/qt5-multimedia/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtmultimedia/lib/libQt5Multimedia.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtmultimedia/lib/libQt5Multimedia.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtmultimedia/lib/libQt5Multimedia.la $(1)/usr/lib/
endef

define Package/qt5-multimediawidgets/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtmultimedia/lib/libQt5MultimediaWidgets.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtmultimedia/lib/libQt5MultimediaWidgets.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtmultimedia/lib/libQt5MultimediaWidgets.la $(1)/usr/lib/
endef

define Package/qt5-network/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Network.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Network.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Network.la $(1)/usr/lib/
endef

define Package/qt5-networkauth/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtnetworkauth/lib/libQt5NetworkAuth.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtnetworkauth/lib/libQt5NetworkAuth.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtnetworkauth/lib/libQt5NetworkAuth.la $(1)/usr/lib/
endef

define Package/qt5-nfc/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtconnectivity/lib/libQt5Nfc.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtconnectivity/lib/libQt5Nfc.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtconnectivity/lib/libQt5Nfc.la $(1)/usr/lib/
endef

define Package/qt5-printsupport/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5PrintSupport.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5PrintSupport.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5PrintSupport.la $(1)/usr/lib/
endef

define Package/qt5-purchasing/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtpurchasing/lib/libQt5Purchasing.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtpurchasing/lib/libQt5Purchasing.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtpurchasing/lib/libQt5Purchasing.la $(1)/usr/lib/
endef

define Package/qt5-positioning/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtlocation/lib/libQt5Positioning.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtlocation/lib/libQt5Positioning.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtlocation/lib/libQt5Positioning.la $(1)/usr/lib/
endef

define Package/qt5-remoteobjects/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtremoteobjects/lib/libQt5RemoteObjects.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtremoteobjects/lib/libQt5RemoteObjects.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtremoteobjects/lib/libQt5RemoteObjects.la $(1)/usr/lib/
endef

define Package/qt5-serialport/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt5SerialPort.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt5SerialPort.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialport/lib/libQt5SerialPort.la $(1)/usr/lib/
endef

define Package/qt5-serialbus/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt5SerialBus.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt5SerialBus.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtserialbus/lib/libQt5SerialBus.la $(1)/usr/lib/
endef

define Package/qt5-sensors/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtsensors/lib/libQt5Sensors.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtsensors/lib/libQt5Sensors.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtsensors/lib/libQt5Sensors.la $(1)/usr/lib/
endef

define Package/qt5-sql/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Sql.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Sql.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Sql.la $(1)/usr/lib/
endef

define Package/qt5-svg/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtsvg/lib/libQt5Svg.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtsvg/lib/libQt5Svg.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtsvg/lib/libQt5Svg.la $(1)/usr/lib/
endef

define Package/qt5-script/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtscript/lib/libQt5Script.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtscript/lib/libQt5Script.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtscript/lib/libQt5Script.la $(1)/usr/lib/
endef

define Package/qt5-scripttools/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtscript/lib/libQt5ScriptTools.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtscript/lib/libQt5ScriptTools.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtscript/lib/libQt5ScriptTools.la $(1)/usr/lib/
endef

define Package/qt5-test/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Test.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Test.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Test.la $(1)/usr/lib/
endef

define Package/qt5-texttospeech/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtspeech/lib/libQt5TextToSpeech.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtspeech/lib/libQt5TextToSpeech.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtspeech/lib/libQt5TextToSpeech.la $(1)/usr/lib/
endef

define Package/qt5-widgets/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Widgets.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Widgets.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Widgets.la $(1)/usr/lib/
endef

define Package/qt5-websockets/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5WebSockets.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5WebSockets.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5WebSockets.la $(1)/usr/lib/
endef

define Package/qt5-webchannel/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtwebchannel/lib/libQt5WebChannel.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtwebchannel/lib/libQt5WebChannel.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtwebchannel/lib/libQt5WebChannel.la $(1)/usr/lib/
endef

define Package/qt5-xml/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Xml.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Xml.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Xml.la $(1)/usr/lib/
endef

define Package/qt5-xmlpatterns/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt5XmlPatterns.so* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt5XmlPatterns.prl $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/qtxmlpatterns/lib/libQt5XmlPatterns.la $(1)/usr/lib/
endef

$(eval $(call BuildPackage,qt5-bluetooth))
$(eval $(call BuildPackage,qt5-charts))
$(eval $(call BuildPackage,qt5-core))
$(eval $(call BuildPackage,qt5-concurrent))
$(eval $(call BuildPackage,qt5-dbus))
$(eval $(call BuildPackage,qt5-gui))
$(eval $(call BuildPackage,qt5-gamepad))
$(eval $(call BuildPackage,qt5-help))
$(eval $(call BuildPackage,qt5-multimedia))
$(eval $(call BuildPackage,qt5-multimediawidgets))
$(eval $(call BuildPackage,qt5-network))
$(eval $(call BuildPackage,qt5-networkauth))
$(eval $(call BuildPackage,qt5-nfc))
$(eval $(call BuildPackage,qt5-printsupport))
$(eval $(call BuildPackage,qt5-purchasing))
$(eval $(call BuildPackage,qt5-positioning))
$(eval $(call BuildPackage,qt5-remoteobjects))
$(eval $(call BuildPackage,qt5-serialport))
$(eval $(call BuildPackage,qt5-serialbus))
$(eval $(call BuildPackage,qt5-sensors))
$(eval $(call BuildPackage,qt5-sql))
$(eval $(call BuildPackage,qt5-svg))
$(eval $(call BuildPackage,qt5-script))
$(eval $(call BuildPackage,qt5-scripttools))
$(eval $(call BuildPackage,qt5-test))
$(eval $(call BuildPackage,qt5-texttospeech))
$(eval $(call BuildPackage,qt5-widgets))
$(eval $(call BuildPackage,qt5-websockets))
$(eval $(call BuildPackage,qt5-webchannel))
$(eval $(call BuildPackage,qt5-xml))
$(eval $(call BuildPackage,qt5-xmlpatterns))
