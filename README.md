Kitkat RK3188 source code from Rikomagic
=============

The kernel
--------

Is GPL kernel from Rikomagic. It has many issues, so the goal of this fork
is to fix these issues as much as possible and make it usable with various
Linux distributions without a bunch of workarounds in the rootfs.

Tested with:
Arch Linux
Debian wheezy (had problems with UDEV)

Installation:

Run 'make-mk802iv-linux-nowifi' script if you have GCC toolchain installed
with versions from 4.3 to 4.7. Do not compile it with 4.8 or 4.9, you will
get broken kernel.

If you don't, cross your fingers and run the script with --download option.
This will get the precompiled Linaro toolchain for you and prepare itself.

Hardware
--------

USB stack
-----

Is the main thing that should work as stable as AK-47 if you want this
working as the home server. Original drivers unfortunately sucks and no
USB wifi adapters is working. The speed with mass storage, however, is
acceptable enough, for example, for burning BLU-rays.

USB stack has two versions of the DWC OTG driver.
v2.7 looks like more stable but with limited hardware support.
v3.1 is not stable.

FIX: Fixed 'buffer not align to 4 bytes' messages with USB wifi adapters
attached. This was because the network stack was allocating buffers not
aligned to 4 bytes which DMA controller is unable to handle. Solution
was to port a workaround from the newer published DWC_OTG driver to
reallocate any unaligned data.

Wifi
-----

Don't waste time and don't try to make it working with default driver from
Rikomagic in this kernel. Better buy a good USB adapter like ALFA AWUS 036h
with old Realtek or Ralink chipsets. Built-in WiFi has not very good signal
strength even if good driver will be adopted. These drivers are good reference
for mainline development.

AP6210
--

Disabled in stable (minimal) configuration.

Bluetooth
-----

Just does not work like in any other Linux distribution based on this kernel.

Display/HDMI
-----

Works acceptable but not without the flaws. Console mapped to the framebuffer
in the config.