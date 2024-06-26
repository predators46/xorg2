include $(TOPDIR)/rules.mk

PKG_NAME:=xrdp
PKG_VERSION:=0.9.25.1
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/neutrinolabs/xrdp/releases/download/v$(PKG_VERSION)/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=eef396b3364e0204723fa0d745376567d598eca43ac5aecfb9e543ca0895e27e

PKG_MAINTAINER:=Esa Aprilia Salsabila <esaapriliasalsabila@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

HOST_BUILD_DEPENDS:=libx11/host libxfixes/host libxrandr/host libice/host
PKG_BUILD_DEPENDS:=xrdp/host

PKG_FIXUP:=autoreconf

HOST_BUILD_PARALLEL:=1
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/xrdp
	SECTION:=xorg
	CATEGORY:=Xorg
	DEPENDS:=+libx11 +libxfixes +libxrandr +libopenssl +libturbojpeg-turbo +libice +libsm
	TITLE:=An open source RDP server
	URL:=http://www.xrdp.org/
endef

define Package/xrdp/description
	xrdp provides a graphical login to remote machines using Microsoft Remote Desktop Protocol (RDP).
endef

CONFIGURE_VARS += \
	TURBOJPEG_PATH="$(STAGING_DIR)/usr"

CONFIGURE_ARGS += \
	--prefix=/usr \
	--disable-pam \
	--enable-tjpeg

HOST_CONFIGURE_ARGS += \
	--x-includes="$(STAGING_DIR_HOSTPKG)/include" \
	--x-libraries="$(STAGING_DIR_HOSTPKG)/lib" \
	--enable-static \
	--disable-shared \
	--disable-pam

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

define Package/xrdp/install
	$(INSTALL_DIR) \
	  $(1)/usr/bin \
	  $(1)/etc/xrdp \
	  $(1)/usr/sbin \
	  $(1)/usr/lib/xrdp

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/bin/* \
	  $(1)/usr/bin/
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/sbin/* \
	  $(1)/usr/sbin/
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/xrdp/*.so* \
	  $(1)/usr/lib/xrdp/
	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/share \
	  $(1)/usr/
	$(CP) \
	  $(PKG_INSTALL_DIR)/etc/xrdp \
	  $(1)/etc/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,xrdp))
