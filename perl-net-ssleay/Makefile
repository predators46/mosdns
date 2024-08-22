include $(TOPDIR)/rules.mk


PKG_NAME:=perl-net-ssleay
PKG_VERSION:=1.94
PKG_RELEASE:=1

PKG_SOURCE:=Net-SSLeay-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://cpan.metacpan.org/authors/id/C/CH/CHRISN/
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/Net-SSLeay-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/perl/perlmod.mk

define Package/perl-net-ssleay
	SUBMENU:=Perl
	SECTION:=lang
	CATEGORY:=Languages
	TITLE:=Perl extension for using OpenSSL
	DEPENDS:=perl +libopenssl +zlib +perlbase-thread +perlbase-base +perlbase-net
	URL:=https://metacpan.org/dist/Net-SSLeay
endef

MOD_CFLAGS_PERL += OPENSSL_PREFIX="$(STAGING_DIR)/usr"

define Build/Configure
	$(call perlmod/Configure,OPENSSL_PREFIX=$(STAGING_DIR)/usr/lib,)
endef

define Build/Compile
	$(call perlmod/Compile,,)
endef

define Package/perl-net-ssleay/install
	$(call perlmod/Install,$(1),Net auto)
endef

$(eval $(call BuildPackage,perl-net-ssleay))
