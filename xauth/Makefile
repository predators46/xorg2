include $(TOPDIR)/rules.mk

PKG_NAME:=xauth
PKG_VERSION:=1.1.3
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://www.x.org/releases/individual/app/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_HASH:=e7075498bae332f917f01d660f9b940c0752b2556a8da61ccb62a44d0ffe9d33

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=util-macros
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/xauth
	SECTION:=apps
	CATEGORY:=Applications
	TITLE:=X.Org authorization settings program
	DEPENDS:=+libx11 +libxau +libxext +libxmu
	URL:=http://xorg.freedesktop.org/
endef

define Package/xauth/description
	X authority file utility
endef

TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS += \
	--prefix=/usr

define Package/xauth/install
	$(INSTALL_DIR) \
	  $(1)/usr/sbin

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/xauth \
	  $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,xauth))
