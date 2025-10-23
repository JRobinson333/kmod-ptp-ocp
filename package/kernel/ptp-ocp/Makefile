nclude $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=ptp-ocp
PKG_RELEASE:=1

define KernelPackage/ptp-ocp
        TITLE:=PTP OCP support
        DEPENDS:=+kmod-ptp +kmod-hwmon-core
        KCONFIG:=CONFIG_PTP_1588_CLOCK_OCP=m
        FILES:=$(LINUX_DIR)/drivers/ptp/ptp_ocp.ko
        AUTOLOAD:=$(call AutoProbe,ptp_ocp)
endef

define KernelPackage/ptp-ocp/description
        Support for Time Appliances Project OCP PTP cards.
endef

$(eval $(call KernelPackage,ptp-ocp))
