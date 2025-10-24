include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/ptp-ocp
  TITLE:=Microchip OCP PTP Clock Support
  DEPENDS:=+kmod-ptp
  KCONFIG:=CONFIG_PTP_1588_CLOCK_OCP
  FILES:=$(PKG_BUILD_DIR)/ptp_ocp.ko
  AUTOLOAD:=$(call AutoLoad,50,ptp_ocp)
  $(call AddDepends/ptp)
endef

define KernelPackage/ptp-ocp/description
  Kernel module for Microchip OCP-based PTP grandmaster clocks.
  Supports hardware timestamping and precise time synchronization.
endef

MAKE_OPTS += \
	ARCH="$(LINUX_KARCH)" \
	CROSS_COMPILE="$(TARGET_CROSS)" \
	SUBDIRS="$(PKG_BUILD_DIR)"

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) -C "$(LINUX_DIR)" \
		$(MAKE_OPTS) \
		modules
endef

$(eval $(call KernelPackage,ptp-ocp))
