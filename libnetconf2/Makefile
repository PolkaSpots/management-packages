#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libnetconf2
PKG_VERSION:=0.4.12
PKG_RELEASE:=1
PKG_REV:=91d68c62d63404431ebdd16874c4a8a42d04afcd
PKG_INSTALL:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/cesnet/libnetconf2/
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_LICENSE:=BSD-3-Clause

PKG_BUILD_DIR=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libnetconf2
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=NETCONF library
  URL:=$(PKG_SOURCE_URL)
  DEPENDS:= \
	+libyang \
	+libssh \
	+libopenssl
endef

define Package/libnetconf2/description
 libnetconf2 is the NETCONF library in C intended for building NETCONF clients and servers.

 libnetconf2 provides basic functions to connect NETCONF client and server to each other via
 SSH, to send and receive NETCONF messages. NETCONF datastore implementation is not included.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/libnetconf2
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libnetconf2/*.h $(1)/usr/include/libnetconf2/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libnetconf2.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/include/libnetconf2
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/libnetconf2/* \
		$(1)/usr/include/libnetconf2/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libnetconf2.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libnetconf2/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libnetconf2.so* \
		$(1)/usr/lib/
	
	$(INSTALL_DIR) $(1)/usr/share/libnetconf2
	$(CP) $(PKG_INSTALL_DIR)/usr/share/libnetconf2/*.yin $(1)/usr/share/libnetconf2/
endef

$(eval $(call BuildPackage,libnetconf2))
