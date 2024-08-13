#
# Copyright (C) 2006-2018 OpenWrt.org 
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=paho.mqtt.c
PKG_VERSION:=v1.3.11
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/eclipse/paho.mqtt.c/archive/refs/tags/$(PKG_VERSION)
PKG_MD5SUM:=ce269af51541148c6e6a50f2763757e4

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/libpaho-mqtt-c
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Eclipse Paho MQTT C Client Library
  URL:=https://eclipse.org/paho/
  DEPENDS:=+libc +libpthread +libssl
endef

define Package/libpaho-mqtt-c/description
  Eclipse Paho MQTT C Client Library
endef

define Build/Configure
  $(call Build/Configure/Default,--prefix=/usr)
endef

define Build/InstallDev
  $(INSTALL_DIR) $(1)/usr/include
  $(CP) $(PKG_BUILD_DIR)/src/*.h $(1)/usr/include/
  $(INSTALL_DIR) $(1)/usr/lib
  $(CP) $(PKG_BUILD_DIR)/build/output/* $(1)/usr/lib/
endef

define Package/libpaho-mqtt-c/install
  $(INSTALL_DIR) $(1)/usr/lib
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/build/output/* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libpaho.mqtt.c))
