# Copyright (C) 2019 Lucian Cristian <lucian.cristian@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=libxcursor
_PKG_NAME:=libXcursor
PKG_VERSION:=1.2.2
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://xorg.freedesktop.org/releases/individual/lib/
PKG_SOURCE:=$(_PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_HASH:=53d071bd2cc56e517a30998d5e685c8a74556ddada43c6985d14da9a023a88ee

PKG_BUILD_DIR:=$(BUILD_DIR)/$(_PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libxcursor
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libxrender +libxfixes
  TITLE:=X Cursor management library
  URL:=http://xorg.freedesktop.org/
endef

TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS += \
  --prefix=/usr \

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/* \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{pkgconfig,*.so*} \
	  $(1)/usr/lib/
endef

define Package/libxcursor/install
	$(INSTALL_DIR) \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libxcursor))
