#
# Copyright (C) 2018 Yousong Zhou <yszhou4tech@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pixman
PKG_VERSION:=0.38.0
PKG_RELEASE:=2
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=a7592bef0156d7c27545487a52245669b00cf7e70054505381cff2136d890ca8
PKG_SOURCE_URL:=https://www.cairographics.org/releases
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING
PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_MAINTAINER:=Yousong Zhou <yszhou4tech@gmail.com>

include $(INCLUDE_DIR)/package.mk


define Package/pixman
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=a low-level software library for pixel manipulation
  URL:=http://www.pixman.org/
endef

define Package/pixman/description
  Pixman is a low-level software library for pixel manipulation, providing
  features such as image compositing and trapezoid rasterization. Important
  users of pixman are the cairo graphics library and the X server.
endef

define Package/pixman/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libpixman*.so* $(1)/usr/lib
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib
endef

$(eval $(call BuildPackage,pixman))
