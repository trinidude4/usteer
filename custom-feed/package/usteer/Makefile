# SPDX-License-Identifier: GPL-2.0-only

include $(TOPDIR)/rules.mk

PKG_NAME:=usteer
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/NilsRo/usteer.git
PKG_SOURCE_DATE:=2024-11-11
PKG_SOURCE_VERSION:=2be670f7a2e7a61b7ff002130d4091714308ca99

PKG_MAINTAINER:=David Bauer <mail@david-bauer.net>
PKG_LICENSE:=GPL-2.0-only

PKG_BUILD_DEPENDS:=libpcap

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/usteer
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libubox +libubus +libblobmsg-json +libnl-tiny
  TITLE:=OpenWrt AP roaming assist daemon
endef

define Package/usteer/conffiles
/etc/config/usteer
endef

define Package/usteer/install
	$(INSTALL_DIR) $(1)/sbin $(1)/etc/init.d $(1)/etc/config

	$(CP) $(PKG_BUILD_DIR)/openwrt/usteer/files/etc/config/usteer $(1)/etc/config/usteer

	$(INSTALL_BIN) $(PKG_BUILD_DIR)/openwrt/usteer/files/etc/init.d/usteer $(1)/etc/init.d/usteer
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/usteerd $(1)/sbin/usteerd
endef

$(eval $(call BuildPackage,usteer))
