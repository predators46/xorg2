# Copyright (C) 2019 Lucian Cristian <lucian.cristian@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=pango
PKG_VERSION:=1.52.2
_PKG_VERSION:=1.52
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://download.gnome.org/sources/$(PKG_NAME)/$(_PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_HASH:=d0076afe01082814b853deec99f9349ece5f2ce83908b8e58ff736b41f78a96b

#PKG_BUILD_DEPENDS:=
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1
#PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/pango
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libexpat +harfbuzz +fribidi +cairo \
	    +libfreetype +libxft +fontconfig
  TITLE:=A library for layout and rendering of text
  URL:=http://www.pango.org
endef

TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS += \
  --prefix=/usr \
  --enable-gtk-doc=no \
  --enable-gtk-doc-html=no \
  --enable-gtk-doc-pdf=no

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib \

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/* \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{pkgconfig,*.so*} \
	  $(1)/usr/lib/
endef

define Package/pango/install
	$(INSTALL_DIR) \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

$(eval $(call BuildPackage,pango))
