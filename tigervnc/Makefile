# Copyright (C) 2019 Lucian Cristian <lucian.cristian@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=tigervnc
PKG_VERSION:=1.13.1
PKG_SOURCE_URL:=https://github.com/TigerVNC/tigervnc/archive/v$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=b7c5b8ed9e4e2c2f48c7b2c9f21927db345e542243b4be88e066b2daa3d1ae25


PKG_BUILD_DEPENDS:=fltk
PKG_BUILD_PARALLEL:=1
CMAKE_INSTALL=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/tigervnc
  SECTION:=xorg
  CATEGORY:=Xorg
  DEPENDS:=+libsm +libx11 +libxext +libice +libjpeg-turbo +perl +zlib \
	+libxdamage +libxfixes +libxrandr +libstdcpp +libxtst
  TITLE:=TigerVNC (Virtual Network Computing)
  URL:=https://www.tigervnc.org/
endef

TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

CMAKE_OPTIONS += \
	-DENABLE_PAM=OFF \
	-DBUILD_VIEWER=OFF

define Package/tigervnc/install
$(INSTALL_DIR) \
	  $(1)/usr/bin

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/* \
	  $(1)/usr/bin/
endef

$(eval $(call BuildPackage,tigervnc))
