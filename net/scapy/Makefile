#
# Copyright (C) 2006-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=scapy
PKG_VERSION:=2.4.3
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/secdev/scapy/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=6cacd9ebe2beeb06b10ff57bff3632222755e9d62f1b38e71b02edab6e71d776

include $(INCLUDE_DIR)/package.mk
include ../../lang/python/python3-package.mk

define Package/scapy
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Interactive packet manipulation tool and network scanner
  MAINTAINER:=W. Michael Petullo <mike@flyn.org>
  URL:=https://scapy.net/
  DEPENDS:=+python3
endef

define Package/scapy/description
  Scapy is a powerful interactive packet manipulation program built on top
  of the Python interpreter. It can be used to forge or decode packets of
  a wide number of protocols, send them over the wire, capture them, match
  requests and replies, and much more.
endef

define Build/Compile
	$(call Python3/ModSetup,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/scapy/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
endef

$(eval $(call BuildPackage,scapy))
