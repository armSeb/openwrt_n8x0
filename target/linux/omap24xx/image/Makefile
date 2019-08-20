#
# Copyright (C) 2010-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Image/Build/Initramfs
    cat $(KDIR)/zImage-initramfs $(DTS_DIR)/omap2420-n810.dtb > $(BIN_DIR)/$(IMG_PREFIX)-zImage-initramfs
endef

define Device/Default
  PROFILES := Default
  DEVICE_VARS :=
  KERNEL_NAME := zImage
  KERNEL := kernel-bin
  KERNEL_INITRAMFS := kernel-bin | lzma | append-dtb
  IMAGES := squashfs
  SUPPORTED_DEVICES = $(subst _,$(comma),$(1))
endef

define Device/n810-base
  DEVICE_TITLE := Nokia N810 (base)
  DEVICE_DTS := omap2420-n810
  KERNEL_INITRAMFS := kernel-bin | lzma | append-dtb
  DEVICE_PACKAGES := \
	block-mount \
        gpsd \
        ip iw kmod-p54-spi wpa-supplicant \
        dnsmasq dropbear \
        pwrtray-backend \
        kmod-fs-vfat kmod-fs-msdos \
        kmod-input-evdev \
        kmod-leds-gpio \
        kmod-usb-gadget-eth \
        kmod-usb-net kmod-usb-net-cdc-ether kmod-usb-net-pegasus kmod-usb-net-rndis \
        kmod-usb-storage kmod-usb-hid \
        kmod-bluetooth kmod-bluetooth-hci-h4p bluez-utils bluez-hcidump \
        kmod-n810bm maemo-kexec calvaria \
        schedtool
endef

TARGET_DEVICES += n810-base

$(eval $(call BuildImage))
