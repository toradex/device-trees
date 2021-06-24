# your kernel sources
STAGING_KERNEL_DIR ?= $(INSTALL_MOD_PATH)/lib/modules/$(KERNELRELEASE)/source/

# kernel output (if building out-of-tree)
KBUILD_OUTPUT ?= $(STAGING_KERNEL_DIR)

DTC_FLAGS := -@

# we have dtbos in arm and arm64 architecture, set the include paths
# to include both architectures.
KERNEL_INCLUDE = " \
    ${STAGING_KERNEL_DIR}/arch/arm/boot/dts/ \
    ${STAGING_KERNEL_DIR}/arch/arm64/boot/dts/*/ \
"

DTS_INCLUDES := $(patsubst %,-I%,$(dir $(wildcard $(KERNEL_INCLUDE))))

HOSTCC := gcc $(DTS_INCLUDES)

PWD := $(shell pwd)

dtb-y += apalis-imx6_atmel-mxt_overlay.dtbo
dtb-y += apalis-imx6_fusion-f0710a_overlay.dtbo
dtb-y += apalis-imx6_hdmi_overlay.dtbo
dtb-y += apalis-imx6_lcd-edt7_overlay.dtbo
dtb-y += apalis-imx6_lcd-lt161010_overlay.dtbo
dtb-y += apalis-imx6_lvds-lt170410_overlay.dtbo
dtb-y += apalis-imx6_stmpe-ts_overlay.dtbo
dtb-y += apalis-imx6_vga_overlay.dtbo
dtb-y += apalis-imx8_ar0521_overlay.dtbo
dtb-y += apalis-imx8_atmel-mxt_overlay.dtbo
dtb-y += apalis-imx8_hdmi_overlay.dtbo
dtb-y += apalis-imx8_lvds_overlay.dtbo
dtb-y += apalis-imx8_ov5640-2_overlay.dtbo
dtb-y += apalis-imx8_ov5640_overlay.dtbo
dtb-y += apalis-imx8x_ad7879_overlay.dtbo
dtb-y += apalis-imx8x_atmel-mxt_overlay.dtbo
dtb-y += apalis-imx8x_display-lcdif_overlay.dtbo
dtb-y += apalis-imx8x_dsihdmi_overlay.dtbo
dtb-y += apalis-imx8x_lvds_overlay.dtbo
dtb-y += apalis-imx8x_ov5640_overlay.dtbo
dtb-y += apalis-imx8x_parallel-rgb_overlay.dtbo
dtb-y += colibri-imx6_atmel-mxt-adapter_overlay.dtbo
dtb-y += colibri-imx6_atmel-mxt-connector_overlay.dtbo
dtb-y += colibri-imx6-eval_spidev_overlay.dtbo
dtb-y += colibri-imx6_fusion-f0710a-adapter_overlay.dtbo
dtb-y += colibri-imx6_fusion-f0710a-connector_overlay.dtbo
dtb-y += colibri-imx6_hdmi_overlay.dtbo
dtb-y += colibri-imx6_lcd-edt7_overlay.dtbo
dtb-y += colibri-imx6_lcd-lt161010_overlay.dtbo
dtb-y += colibri-imx6_lcd-lt170410_overlay.dtbo
dtb-y += colibri-imx6_lcd-vga_overlay.dtbo
dtb-y += colibri-imx6_stmpe-ts_overlay.dtbo
dtb-y += colibri-imx7_ad7879_overlay.dtbo
dtb-y += colibri-imx7_atmel-mxt-adapter_overlay.dtbo
dtb-y += colibri-imx7_atmel-mxt-connector_overlay.dtbo
dtb-y += colibri-imx7_disable-uart-b_overlay.dtbo
dtb-y += colibri-imx7-eval_spidev_overlay.dtbo
dtb-y += colibri-imx7_fusion-f0710a-adapter_overlay.dtbo
dtb-y += colibri-imx7_fusion-f0710a-connector_overlay.dtbo
dtb-y += colibri-imx7_lcd-edt7_overlay.dtbo
dtb-y += colibri-imx7_lcd-lt161010_overlay.dtbo
dtb-y += colibri-imx7_lcd-lt170410_overlay.dtbo
dtb-y += colibri-imx7_lcd-vga_overlay.dtbo
dtb-y += colibri-imx8x_ad7879_overlay.dtbo
dtb-y += colibri-imx8x_atmel-mxt-adapter_overlay.dtbo
dtb-y += colibri-imx8x_atmel-mxt-connector_overlay.dtbo
dtb-y += colibri-imx8x_display-lcdif_overlay.dtbo
dtb-y += colibri-imx8x_dsihdmi_overlay.dtbo
dtb-y += colibri-imx8x-eval_spidev_overlay.dtbo
dtb-y += colibri-imx8x_ov5640_overlay.dtbo
dtb-y += colibri-imx8x_parallel-rgb_overlay.dtbo
dtb-y += colibri-imx8x_parallel-rgb-lvds_overlay.dtbo
dtb-y += display-dpi-lt170410_overlay.dtbo
dtb-y += display-edt5.7_overlay.dtbo
dtb-y += display-edt7_overlay.dtbo
dtb-y += display-fullhd-imx6_overlay.dtbo
dtb-y += display-fullhd_overlay.dtbo
dtb-y += display-lt161010_overlay.dtbo
dtb-y += display-lt170410_overlay.dtbo
dtb-y += display-vga_overlay.dtbo
dtb-y += touch-atmel-mxt_overlay.dtbo
dtb-y += verdin-imx8mm_lt8912_overlay.dtbo
dtb-y += verdin-imx8mm_ov5640_overlay.dtbo
dtb-y += verdin-imx8mm_sn65dsi84-lt170410_overlay.dtbo
dtb-y += verdin-imx8mm_sn65dsi84_overlay.dtbo
dtb-y += verdin-imx8mp_lt8912_overlay.dtbo
dtb-y += verdin-imx8mp_native-hdmi_overlay.dtbo
dtb-y += verdin-imx8mp_ov5640_overlay.dtbo
dtb-y += verdin-imx8mp_sn65dsi84-lt170410_overlay.dtbo
dtb-y += verdin-imx8mp_sn65dsi84_overlay.dtbo

targets += $(dtb-y)
always  := $(dtb-y)

# adopted to dtbo from scripts/Makefile.lib
$(obj)/%.dtbo: $(src)/%.dts $(DTC) FORCE
	$(call if_changed_dep,dtc,dtb)

all:
	make -C $(KBUILD_OUTPUT) M=$(PWD)

clean:
	make -C $(KBUILD_OUTPUT) M=$(PWD) clean
