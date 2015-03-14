#
# Copyright (C) 2006-2011 OpenWrt.org
# Copyright (C) 2014 Yang Li
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=l4proxy
PKG_VERSION:=0.0.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/BillLeecn/l4proxy.git
PKG_SOURCE_VERSION:=d214dd9d4a49ec7fa2bd9d3fd89f2aee7e085ff4
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_USE_MIPS16:=0
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/l4proxy
  SECTION:=net
  CATEGORY:=Network
  #DEPENDS:=
  TITLE:=Layer-4 Proxy
endef

define Package/l4proxy/description
  a transparent layer-4 proxy for masking network stack characteristcs
endef

define Package/l4proxy/conffiles
/etc/default/l4proxyd
endef

define Package/l4proxy/install
	$(INSTALL_DIR) $(1)/etc/default
	$(INSTALL_CONF) ./files/l4proxyd.default $(1)/etc/default/l4proxyd
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/l4proxyd.init $(1)/etc/init.d/l4proxyd
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/src/l4proxyd $(1)/usr/bin/
endef

$(eval $(call BuildPackage,l4proxy))
