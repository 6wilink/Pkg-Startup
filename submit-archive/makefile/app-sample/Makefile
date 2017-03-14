# 6Harmonics Inc
# maintainer: Qige Zhao

include $(TOPDIR)/rules.mk

APP_NAME:=app-demo
PKG_NAME:=app-sample
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)_$(PKG_VERSION)-$(PKG_RELEASE)

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION)-$(PKG_RELEASE).tar.bz2
PKG_SOURCE_URL:=http://10.10.1.151/qz/app-sample/ \
	http://10.10.1.150/openwrt/dl/app-sample/
PKG_MD5SUM:=c97874ef5854e577a1486ba961cfd2e4

#PKG_FIXUP:=libtool
#PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Application sample of package
  MAINTAINER:=Qige Zhao <qigezhao@gmail.com>
#  DEPENDS:=+libiwinfo
endef

define Package/$(PKG_NAME)/description
  Application sample when start a new package.
  Including Makefile, base structure, description.
  And a startup main() function.
endef


define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/usr/sbin

	$(INSTALL_CONF) $(PKG_BUILD_DIR)/$(PKG_NAME).conf 	$(1)/etc/config/$(APP_NAME)
	$(INSTALL_BIN) 	$(PKG_BUILD_DIR)/$(PKG_NAME).init 	$(1)/etc/init.d/$(APP_NAME)
	$(INSTALL_BIN) 	$(PKG_BUILD_DIR)/$(APP_NAME) 		$(1)/usr/sbin/$(APP_NAME)
endef

$(eval $(call BuildPackage,$(PKG_NAME)))