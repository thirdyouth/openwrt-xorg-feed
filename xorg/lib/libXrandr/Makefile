#
# Copyright (C) 2007-2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libXrandr
PKG_RELEASE:=5
PKG_VERSION:=1.5.1

PKG_SOURCE_URL:=http://xorg.freedesktop.org/releases/individual/lib/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/$(PKG_NAME)-$(PKG_VERSION)/
PKG_HASH:=1ff9e7fa0e4adea912b16a5f0cfa7c1d35b0dcda0e216831f7715c8a3abcf51a

PKG_FIXUP:=libtool
PKG_INSTALL:=1
PKG_BUILD_DEPENDS:=randrproto renderproto xextproto

include $(INCLUDE_DIR)/package.mk

define Package/libXrandr
  SECTION:=xorg-libraries
  CATEGORY:=Xorg
  SUBMENU:=libraries
  DEPENDS:=+libXext +libXrender +libX11
  TITLE:=libXrandr
  URL:=http://xorg.freedesktop.org/
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--enable-malloc0returnsnull \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/X11/extensions}
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,a,la} \
		$(1)/usr/lib/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/X11/extensions/* \
		$(1)/usr/include/X11/extensions/
endef

define Package/libXrandr/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libXrandr))
