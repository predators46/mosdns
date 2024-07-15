include $(TOPDIR)/rules.mk

PKG_NAME:=qtbase
PKG_VERSION:=5.15.14
PKG_RELEASE:=1

PKG_SOURCE:=qtbase-everywhere-opensource-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/official_releases/qt/5.15/5.15.14/submodules/
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PKG_BUILD_DIR=$(BUILD_DIR)/qtbase-everywhere-src-$(PKG_VERSION)

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

EXTRA_CFLAGS += $(FPIC) -ffunction-sections -fdata-sections -flto
EXTRA_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS = \
	-sysroot $(STAGING_DIR) \
	-extprefix /usr \
	-hostprefix $(STAGING_DIR_HOSTPKG) \
	-bindir /usr/bin \
	-headerdir /usr/include/qt \
	-libdir /usr/lib \
	-archdatadir /usr/lib/qt \
	-plugindir /usr/lib/qt/plugins \
	-libexecdir /usr/lib/qt/libexec \
	-importdir /usr/lib/qt/imports \
	-qmldir /usr/lib/qt/qml \
	-datadir /usr/share/qt \
	-docdir /usr/share/doc/qt \
	-translationdir /usr/share/qt/translations \
	-sysconfdir /etc/xdg \
	-examplesdir /usr/share/qt/examples \
	-testsdir /usr/share/qt/tests \
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
	-v

define Build/Compile
	$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR)
endef

define Build/Install
	$(MAKE) -C $(PKG_BUILD_DIR) INSTALL_ROOT=$(PKG_INSTALL_DIR) install
endef

define Package/qtbase/install
	$(INSTALL_DIR) \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{*.so*,*.prl,*.la} \
	  $(1)/usr/lib/
endef

$(eval $(call BuildPackage,qtbase))
