include $(TOPDIR)/rules.mk

PKG_NAME:=libxrandr
PKG_VERSION:=1.5.4
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://www.x.org/releases/individual/lib/
PKG_SOURCE:=libXrandr-$(PKG_VERSION).tar.xz
PKG_HASH:=1ad5b065375f4a85915aa60611cc6407c060492a214d7f9daf214be752c3b4d3

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/libXrandr-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/libXrandr-$(PKG_VERSION)

HOST_BUILD_DEPENDS:=libx11/host libxrender/host libxext/host

HOST_BUILD_PARALLEL:=1
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/libxrandr
	SECTION:=libs
	CATEGORY:=Libraries
	DEPENDS:=+libx11 +libxrender +libxext
	TITLE:=X11 RandR extension library
	URL:=http://xorg.freedesktop.org/
endef

define Package/libxrandr/description
	libXrandr - X Resize, Rotate and Reflection extension library
endef

TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

CONFIGURE_ARGS += \
	--enable-malloc0returnsnull \
	--prefix=/usr

HOST_CONFIGURE_ARGS += \
	--enable-static \
	--disable-shared \
	--enable-malloc0returnsnull

define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/X11 \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{pkgconfig,*.so*} \
	  $(1)/usr/lib/
endef

define Package/libxrandr/install
	$(INSTALL_DIR) \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,libxrandr))
