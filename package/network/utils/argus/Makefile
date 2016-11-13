#
# Copyright (C) 2007-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=argus
PKG_VERSION:=3.0.8.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.qosient.com/argus/src/
PKG_MD5SUM:=eaf5f5ec66569e556392802a70ef9ca5

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_PARALLEL:=1

PKG_MAINTAINER:=Carter Bullard <carter@qosient.com>
PKG_LICENSE:=GPL-2.0

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/argus
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpcap +libpthread +zlib +librpc
  TITLE:=Network Audit Record Generation and Utilization System 
  URL:=http://www.qosient.com/
endef

define Package/bridge/description
  Network Audit Record Generation and Utilization System
endef

define Build/Configure
  $(call Build/Configure/Default)
endef

define Package/samba36-server/conffiles
	/etc/argus.conf
endef

define Package/argus/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/argus.init $(1)/etc/init.d/argus
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/argus.conf $(1)/etc/config/argus
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/argus $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,argus))
