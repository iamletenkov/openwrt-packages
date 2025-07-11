include $(TOPDIR)/rules.mk

PKG_NAME:=rc.cloud
PKG_VERSION:=0.4
PKG_RELEASE:=1
PKG_LICENSE:=MIT
PKG_MAINTAINER:=Ivan Letenkov <ivan@example.com>

include $(INCLUDE_DIR)/package.mk

define Package/rc.cloud
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Minimal cloud-init implementation for OpenWrt
  DEPENDS:=+bash +curl +mount-utils +coreutils-stat +coreutils-base64 +uci
endef

define Package/rc.cloud/description
A very small “cloud-init” for OpenWrt.

* Config-Drive (cidata ISO/blk-dev) – hostname, root password, network-config
* Metadata-service (EC2/OpenStack/Hetzner, optional)
* Kernel flag `ds=nocloud` to disable metadata probing
endef

# ----------- build -------------

define Build/Prepare
	# скрипты/конфиги в $(PKG_BUILD_DIR) — чтобы pkg-install мог их скопировать
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./files/* $(PKG_BUILD_DIR)/
endef

# ничего компилировать не нужно
define Build/Compile
	true
endef

# ----------- install -------------

define Package/rc.cloud/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/rc.cloud $(1)/etc/init.d/rc.cloud
endef

$(eval $(call BuildPackage,rc.cloud))
