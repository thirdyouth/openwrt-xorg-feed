#
# Copyright (C) 2007-2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xf86-input-evdev
PKG_RELEASE:=2
PKG_VERSION:=2.10.5

PKG_SOURCE_URL:=http://xorg.freedesktop.org/releases/individual/driver
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_BUILD_DIR:=$(BUILD_DIR)/Xorg/$(PKG_NAME)-$(PKG_VERSION)/
PKG_MD5SUM:=94c2c8354c74ab1cfbbb0a222078b9c6

PKG_FIXUP:=libtool
PKG_INSTALL:=1

PKG_BUILD_DEPENDS:=randrproto inputproto xproto

include $(INCLUDE_DIR)/package.mk
$(call include_mk, xorg-driver.mk)

define Package/xf86-input-evdev
  SECTION:=xorg-driver
  CATEGORY:=Xorg
  SUBMENU:=driver
  DEPENDS:=+xserver-xorg +mtdev
  TITLE:=xf86-input-evdev
  URL:=http://xorg.freedesktop.org/
endef

define Package/xf86-input-evdev/install
	$(INSTALL_DIR) $(1)/usr/lib/xorg/modules/input
	$(INSTALL_DIR) $(1)/usr/share/X11/xorg.conf.d
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/xorg/modules/input/evdev_drv.so \
		$(1)/usr/lib/xorg/modules/input/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/X11/xorg.conf.d/*.conf \
		$(1)/usr/share/X11/xorg.conf.d/
endef

$(eval $(call BuildPackage,xf86-input-evdev))

