# Copyright (C) 2019 Lucian Cristian <lucian.cristian@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=xf86-input-mouse
PKG_VERSION:=1.9.5
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://www.x.org/releases/individual/driver/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_HASH:=4fde8ae9b44352e2a208584c36528ee3ed13cf5fe4417208a9785daccefd9968

PKG_BUILD_PARALLEL:=1
#PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/xf86-input-mouse
  SECTION:=xorg
  CATEGORY:=Xorg
  DEPENDS:=+libxi +xorg-server +libxkbfile +libxrandr
  TITLE:=X.org mouse input driver
  URL:=https://www.x.org
endef

LDFLAGS:="$LDFLAGS -Wl,-z,lazy"

CONFIGURE_ARGS += \
  --prefix=/usr

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_BUILD_DIR)/include/*.h \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{pkgconfig,xorg/modules/input/*.so*} \
	  $(1)/usr/lib/
endef

define Package/xf86-input-mouse/install
	$(INSTALL_DIR) \
	  $(1)/usr/lib/xorg/modules/input

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/xorg/modules/input/*.so* \
	  $(1)/usr/lib/xorg/modules/input/
endef

$(eval $(call BuildPackage,xf86-input-mouse))
