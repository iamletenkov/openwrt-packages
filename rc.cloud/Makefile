include $(TOPDIR)/rules.mk

PKG_NAME:=rc.cloud
PKG_VERSION:=0.4
PKG_RELEASE:=1

PKG_MAINTAINER:=Ilya Letenkov <iamletenkov@gmail.com>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/rc.cloud
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Minimal cloud-init for OpenWrt
  DEPENDS:=+logd
endef

define Package/rc.cloud/description
Tiny replacement for cloud-init:
• Находит config-drive (CIDATA) или metadata-service
• Применяет hostname, root-пароль, SSH-ключи
• Читает network-config и настраивает сети (WAN/LAN…)
endef

define Package/rc.cloud/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/rc.cloud-setup    $(1)/etc/init.d/rc.cloud-setup
	$(INSTALL_BIN) ./files/rc.cloud-userdata $(1)/etc/init.d/rc.cloud-userdata
	$(INSTALL_BIN) ./files/rc.cloud-final    $(1)/etc/init.d/rc.cloud-final
endef

$(eval $(call BuildPackage,rc.cloud))
