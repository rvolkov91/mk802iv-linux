Kitkat RK3188 source code from Rikomagic
_with workarounds to make it usable with Linux distributions_

1. The kernel

Is old and unstable. To use the device as a server, some unstable
functionality should be disabled.

Do not compile it with GCC 4.9.x toolchain. You can get the broken kernel.
Tested with GCC 4.7.x Debian arm-linux-gnueabihf toolchain.

Should work with any Linux distribution which supports ARMv7.

Tested with:
Arch Linux
Debian wheezy (had problems with UDEV)

2. Hardware

2.1 USB stack

Is the main thing that should work as stable as AK-47 if you want this
working as the home server. Original drivers unfortunately sucks and no
USB wifi adapters is working. The speed with mass storage, however, is
acceptable enough, for example, for burning BLU-rays. As many as possible
hardware returned back from the Linux kernel.

USB stack has two versions of the DWC OTG driver.
v2.7 looks like more stable but with limited hardware support. There is
a workaround to make USB WiFi adapters working ('buffer not align to 4 bytes'
message).
v3.1 is not stable.

2.2 Wifi

The stock driver for AP6210 should be disabled. It was not designed for
work and just like the pain in the ass. Don't waste time and buy a good USB
adapter like ALFA AWUS036 with old Realtek\Atheros chipsets. Even if there
will be a good driver, the signal strengh will not be good enough. There is
a couple of good adapters returned back from the Linux 3.0.36 kernel.
Don't buy adapters with new chipsets since the kernel is old.

2.2.1 AP6210

The driver is not usable with Linux. Only for reference purposes for mainline.

2.3 Bluetooth

Just does not work like in any other Linux distribution based on this kernel.

2.4 Display/HDMI

Works acceptable but not without the flaws. Console mapped to the framebuffer
in the config.