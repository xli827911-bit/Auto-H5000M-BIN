include $(TOPDIR)/rules.mk

PKG_NAME:=higoros-blob
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/higoros-blob
  SECTION:=admin
  CATEGORY:=Hiveton
  TITLE:=Hiveton HiGOOS binary layer
  DEPENDS:=+lua54 +libuci +libubus +libubox +luci-lib-jsonc
endef

define Build/Prepare
    mkdir -p $(PKG_BUILD_DIR)
    wget -q -O - https://github.com/xli827911-bit/Auto-H5000M-BIN/releases/download/higoros-layer/higoros-layer.tar.gz | tar -xz -C $(PKG_BUILD_DIR)/
endef

define Build/Compile
endef

define Package/higoros-blob/conffiles
/etc/config/uhttpd
endef

define Package/higoros-blob/install
    $(CP) $(PKG_BUILD_DIR)/usr $(1)/
    $(CP) $(PKG_BUILD_DIR)/www $(1)/
    $(CP) $(PKG_BUILD_DIR)/etc $(1)/
    chmod +x $(1)/usr/bin/higorosd 2>/dev/null || true
    chmod +x $(1)/etc/init.d/higoros 2>/dev/null || true
endef

$(eval $(call BuildPackage,higoros-blob))
