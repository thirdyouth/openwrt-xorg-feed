#
# Copyright (C) 2007-2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# blogic@openwrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=sato-icon-theme
PKG_RELEASE:=1
PKG_VERSION:=1.0
PKG_SOURCE_URL:=https://github.com/suwus/sato-icon-theme.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2019-11-19
PKG_SOURCE_VERSION:=b9f02989310a3c920589f1aa646bcbf16b2572a0
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_FIXUP:=libtool

PKG_BUILD_DEPENDS:=icon-naming-utils/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

PKG_INSTALL:=1

define Package/sato-icon-theme
  SECTION:=xorg-matchbox
  CATEGORY:=Xorg
  SUBMENU:=Matchbox Window manager
  TITLE:=sato-icon-theme
  DEPENDS:=
  URL:=http://matchbox-project.org
endef

define Package/sato-icon-theme/description
 Matchbox Sato Icon Theme
endef

UTILS_PATH:=$(STAGING_DIR_HOSTPKG)/usr/lib

MAKE_FLAGS += \
    ICONMAP="$(UTILS_PATH)/icon-name-mapping"

define Build/Compile
	make -e -C $(PKG_BUILD_DIR) $(MAKE_FLAGS)
	DESTDIR=$(PKG_INSTALL_DIR) $(MAKE) -C $(PKG_BUILD_DIR) $(MAKE_FLAGS) install
endef

define Package/sato-icon-theme/install
	$(INSTALL_DIR) $(1)/usr/share/icons/Sato
	$(CP) -r \
		$(PKG_INSTALL_DIR)/usr/share/icons/Sato/* \
		$(1)/usr/share/icons/Sato/
endef

$(eval $(call BuildPackage,sato-icon-theme))