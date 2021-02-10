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

dtb-y += apalis-imx6_adv7280_overlay.dtbo
dtb-y += apalis-imx6_atmel-mxt_overlay.dtbo
dtb-y += apalis-imx6_hdmi_overlay.dtbo
dtb-y += apalis-imx6_lvds_overlay.dtbo
dtb-y += apalis-imx6_ov5640_overlay.dtbo
dtb-y += apalis-imx6_ov5640-v11a_overlay.dtbo
dtb-y += apalis-imx6_parallel-rgb_overlay.dtbo
dtb-y += apalis-imx6_stmpe-ts_overlay.dtbo
dtb-y += apalis-imx6_vga_overlay.dtbo
dtb-y += colibri-imx6-aster_atmel-mxt_overlay.dtbo
dtb-y += colibri-imx6-eval_atmel-mxt_overlay.dtbo
dtb-y += colibri-imx6_parallel-rgb_overlay.dtbo
dtb-y += colibri-imx6_stmpe-ts_overlay.dtbo
dtb-y += colibri-imx7_ad7879_overlay.dtbo
dtb-y += colibri-imx7-aster_atmel-mxt_overlay.dtbo
dtb-y += colibri-imx7-eval_atmel-mxt_overlay.dtbo
dtb-y += colibri-imx7_parallel-rgb_overlay.dtbo
dtb-y += display-edt5.7_overlay.dtbo
dtb-y += display-edt7_overlay.dtbo
dtb-y += display-lt161010_overlay.dtbo
dtb-y += display-lt170410_overlay.dtbo

targets += $(dtb-y)
always  := $(dtb-y)

# adopted to dtbo from scripts/Makefile.lib
$(obj)/%.dtbo: $(src)/%.dts $(DTC) FORCE
	$(call if_changed_dep,dtc,dtb)

all:
	make -C $(KBUILD_OUTPUT) M=$(PWD)

clean:
	make -C $(KBUILD_OUTPUT) M=$(PWD) clean
