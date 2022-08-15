#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qcontrol
PKG_VERSION:=0.5.7


PKG_SOURCE=$(PKG_NAME)_$(PKG_VERSION).orig.tar.gz
PKG_SOURCE_URL=http://deb.debian.org/debian/pool/main/q/$(PKG_NAME)/
PKG_HASH=ecc6977266531571e724146fe18478a3a4a168a8a766c47439c4a63b3f73aa3f
#PKG_SUBDIR:=$(PKG_NAME)-$(PKG_RELEASE)
#PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SUBDIR)


PKG_MAINTAINER:=Audun Gangstø <audun@gangsto.org>
PKG_LICENSE:=GPL-3.0

include $(INCLUDE_DIR)/package.mk

define Package/qcontrol
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=qcontrol
  DEPENDS:=+liblua +kmod-input-evdev
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include

define Package/qcontrol/conffiles
	/etc/qcontrol.conf
endef

#define Build/Prepare
#	bash -c env
#	$(TAR) -xz -C $(PKG_BUILD_DIR) -f $(DL_DIR)/$(PKG_SOURCE)
#endef

define Build/Configure
endef

#define Build/Compile
#       make -C  $(PKG_BUILD_DIR) qcontrol
#endef


define Package/qcontrol/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/init.d $(1)/etc/config
	$(INSTALL_BIN) ./files/qcontrol.init $(1)/etc/init.d/qcontrol
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/qcontrol $(1)/usr/sbin/
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/examples/ts219.lua $(1)/etc/qcontrol.conf
endef

$(eval $(call BuildPackage,qcontrol))
