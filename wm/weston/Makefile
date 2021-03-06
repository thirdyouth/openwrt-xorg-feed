#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=weston
PKG_VERSION:=6.0.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://wayland.freedesktop.org/releases/
PKG_MD5SUM:=7c634e262f8a464a076c97fd50ad36b3

PKG_INSTALL:=1
PKG_FIXUP:=libtool

PKG_CONFIG_DEPENDS := \
	CONFIG_WESTON_LAUNCH=y

PKG_BUILD_DEPENDS:=wayland-protocols/host

include $(INCLUDE_DIR)/package.mk

define Package/weston
  SECTION:=weston
  CATEGORY:=Wayland
  TITLE:=weston window manager

  DEPENDS:=@!avr32 @DISPLAY_SUPPORT +libinput +pixman \
	+libxkbcommon +libpng +cairo +libjpeg +libpam \
	+xkbdata +wayland \
	+libdrm +libgl-mesa-egl +libgl-mesa-gles-v2 \
	+libXcursor +libxcb-composite +libxcb-shape +libxcb-xfixes \
	+pango
  URL:=https://wayland.freedesktop.org/
endef

CONFIGURE_ARGS+= \
	--disable-documentation \
	--enable-fbdev-compositor \
	--enable-autotools \
	--enable-weston-launch \
	--disable-setuid-install \
	WAYLAND_PROTOCOLS_DATADIR="${STAGING_DIR}/usr/share/wayland-protocols" \
	--enable-wayland-compositor \
	--enable-drm-compositor \
	--disable-x11-compositor

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.{so*,la} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/{libweston-6,weston}
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libweston-6/*.{so*,la} $(1)/usr/lib/libweston-6/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/weston/*.{so*,la} $(1)/usr/lib/weston/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig/
	
	$(INSTALL_DIR) $(1)/usr/include/{libweston-6,weston}
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/libweston-6/* $(1)/usr/include/libweston-6/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/weston/* $(1)/usr/include/weston/

	$(INSTALL_DIR) $(1)/usr/share/pkgconfig/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/pkgconfig/* $(1)/usr/share/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/share/weston/protocols/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/weston/protocols/* $(1)/usr/share/weston/protocols/
endef

define Package/weston/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/weston-* $(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/libweston-6/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libweston-6/*.so* $(1)/usr/lib/libweston-6/

	$(INSTALL_DIR) $(1)/usr/lib/weston/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/weston/*.so* $(1)/usr/lib/weston/

	$(INSTALL_DIR) $(1)/usr/share/wayland-sessions/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/wayland-sessions/* $(1)/usr/share/wayland-sessions/

	$(INSTALL_DIR) $(1)/usr/share/weston/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/weston/*.png $(1)/usr/share/weston/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/weston/*.svg $(1)/usr/share/weston/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/etc/weston
	$(INSTALL_DATA) ./files/weston.ini $(1)/etc/weston/weston.ini

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/weston.config $(1)/etc/config/weston
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/weston.init $(1)/etc/init.d/weston
endef

$(eval $(call BuildPackage,weston))
