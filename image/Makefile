SHELL = /bin/bash -e

ARCH = $(shell ./tools/arch-tag)
COMPILE_CLEAN ?= clean
WORK_DIR ?= /mnt/extra/tmp/horizon-raspbian-image
IMAGE_OUTPUT_DIR ?= /mnt/extra

all: sd-image

clean: clean-pi2 clean-pi3

clean-%:
	-rm -rf $(IMAGE_OUTPUT_DIR)/horizon-raspbian-$*-*
	-rm -rf $(WORK_DIR)/*

deep-clean:
	tools/deep-clean CLEAN

repo-fork-sync:
	tools/repo-fork-sync

%-sd-image:
	mkdir -p $(WORK_DIR)
	bash -x sd-image/package-sd-image $* $(WORK_DIR) $(IMAGE_OUTPUT_DIR)

push-%-sd-image:
	cd $(IMAGE_OUTPUT_DIR); \
		export IMG=$$(ls ./horizon-raspbian-$*-*.img); \
		zip -8 $$IMG.zip $$IMG; \
		swift upload --verbose colonus $$IMG.zip

.PHONY: clean deep-clean repo-fork-sync sd-image push-sd-image
