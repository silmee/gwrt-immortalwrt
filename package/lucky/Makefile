#
# OpenWrt package: Lucky (https://github.com/gdy666/lucky)
#
# Lucky ships no OpenWrt package upstream: the release tarball contains a
# single fully static x86_64 binary plus systemd/init shims. This package
# installs that binary as-is (no compilation), a procd init script and the
# /etc/lucky working directory; the service creates lucky.conf itself on first
# start (default: http://<ip>:16601, account/password 666).
#
# The binary is fetched by the workflow into ./files/lucky before the build.
#
# This file is free software, licensed under the GNU General Public License v3
# or later.

include $(TOPDIR)/rules.mk

PKG_NAME:=lucky
PKG_VERSION:=3.5.0
PKG_RELEASE:=1
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/lucky
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=Lucky - reverse proxy, DDNS and port forwarding (static x86_64)
  URL:=https://github.com/gdy666/lucky
  LICENSE:=Apache-2.0
  PKGARCH:=x86_64
  DEPENDS:=+ca-bundle
endef

define Package/lucky/description
 Lucky: DDNS, reverse proxy, port forwarding, Web service and network
 tooling in one binary. Prebuilt static x86_64 release binary from
 gdy666/lucky, installed unchanged; the Web UI is embedded and listens on
 port 16601 (default account and password: 666).
endef

define Build/Compile
endef

define Package/lucky/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/lucky $(1)/usr/bin/lucky
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/lucky.init $(1)/etc/init.d/lucky
	$(INSTALL_DIR) $(1)/etc/lucky
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/99_lucky $(1)/etc/uci-defaults/99_lucky
endef

$(eval $(call BuildPackage,lucky))
