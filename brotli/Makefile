include $(TOPDIR)/rules.mk

PKG_NAME:=brotli
PKG_VERSION:=1.1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/google/brotli/archive/v$(PKG_VERSION)
PKG_HASH:=skip

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=python-setuptools-scm/host
#CMAKE_BINARY_SUBDIR := build

PKG_BUILD_PARALLEL:=1

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/brotli
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Brotli compression format
	DEPENDS:=
	URL:=https://github.com/google/brotli
endef

define Package/brotli/description
	Brotli is a generic-purpose lossless compression algorithm that compresses data using a combination of a modern variant of the LZ77 algorithm,
	Huffman coding and 2nd order context modeling, with a compression ratio comparable to the best currently available general-purpose compression methods.
	It is similar in speed with deflate but offers more dense compression.
endef

CMAKE_OPTIONS += \
	-DBUILD_SHARED_LIBS=ON

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/brotli \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{pkgconfig,*.so*} \
	  $(1)/usr/lib/
endef

define Package/brotli/install
	$(INSTALL_DIR) \
	  $(1)/usr/bin \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/brotli \
	  $(1)/usr/bin/
	
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

define Package/python3-brotli
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python bindings for the Brotli compression library
  URL:=https://github.com/google/brotli
  DEPENDS:=+python3 +brotli
endef

define Package/python3-brotli/description
  Generic lossless compressor (python bindings)
endef

$(eval $(call BuildPackage,brotli))
$(eval $(call Py3Package,python3-brotli))
$(eval $(call BuildPackage,python3-brotli))
$(eval $(call BuildPackage,python3-brotli-src))
