include $(TOPDIR)/rules.mk

PKG_NAME:=rc.cloud
PKG_VERSION:=0.4
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/rc.cloud
  SECTION:=base
  CATEGORY:=Base system
  TITLE:=Minimal cloud-init replacement (Config-Drive on /dev/sr0)
  DEPENDS:=+blkid +wget +jq +kmod-fs-vfat +bash +jq +util-linux +coreutils +mount-utils
endef

define Package/rc.cloud/description
Tiny shell scripts, emulating a subset of cloud-init for OpenWrt.
Reads meta-data, user-data, network-config from a Config-Drive ISO
(`/dev/sr0`, label “cidata” / “config-2”) exactly like Proxmox NoCloud
и применяет их при первой загрузке.
endef

define Build/Prepare
	# исходников нет – ничего подготавливать
	mkdir -p $(PKG_BUILD_DIR)
endef
Build/Compile:= # nothing to build

define Package/rc.cloud/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/etc/init.d/rc.cloud-setup    $(1)/etc/init.d/
	$(INSTALL_BIN) ./files/etc/init.d/rc.cloud-userdata $(1)/etc/init.d/
	$(INSTALL_BIN) ./files/etc/init.d/rc.cloud-final    $(1)/etc/init.d/
endef

$(eval $(call BuildPackage,rc.cloud))
