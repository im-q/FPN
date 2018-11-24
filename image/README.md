# raspbian-image

## Introduction

This project creates a filesystem image for a Raspberry Pi3 or Pi2 from a recent Raspbian upstream image. You can download an already-built system image for various SBCs at https://bluehorizon.network.

Related Projects:

* `anax` (http://github.com/open-horizon/anax): The client control application in the Horizon system
* `horizon-pkg` (http://github.com/open-horizon/horizon-pkg): A system for packaging Horizon system `deb`s for multiple distributions and architectures. It also produces Ubuntu snaps

## Operations

### Create SD card image

#### Preconditions

* Execution on an armhf device (often we build on Odroid XU4 or Odroid C2 SBCs)
* You must have the following Linux modules loaded:
  * `dm_multipath`
* You must have the following tools available (among common GNU tools):
  * `kpartx`
  * `parted`
  * `zip`
  * `unzip`
  * `wget`

#### Steps

* Execute `make pi3-sd-image` to make an official, Pi3-only image or `make pi2-sd-image` to make a Pi2 image. The resulting image will be written to /mnt/extra. If you'd like to change the output location, execute `make pi3-sd-image IMAGE_OUTPUT_DIR=/tmp/`.
