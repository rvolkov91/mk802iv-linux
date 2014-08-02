Kitkat RK3188 source code from Rikomagic

Configured to use with MK802IV with AP6210 wifi chipset.

With some modifications in hopes to make MK802IV stick working as quad-core
home server and WIFI router.

Experience with Debian:

Facts:
+Quad-core Cortex A9 is fast enough.
+USB stack works acceptable enough, at 10Mb/sec+ speed. Tested with:
USB HDD & Blu-ray USB writer, various USB wifi adapters, keyboard, mice.
+Console mapped to the primary framebuffer device.
Change the parameter script to disable FIQ console to get FB console working
at boot time.

Known problems:
-The kernel is unstable and old.
-Every change in config can break the build.
-Disabling devtmpfs and using udev instead will crash the kernel. The devtmpfs
is deprecated and should not be used in newer systems. Udev will not start
and you need to restart it manually or from rc.local. The bug should be
somewhere in the display driver.
-Encryption does not work with hostapd (tested on AP6210 and Realtek USB
adapter AWUS036H). I don't know what's this, only open network does work.
-USB OTG driver is unstable and can panic the kernel.
-AP6210 WIFI driver has problems
-No bluetooth

Conclusion:
This device NEEDS normal mainline support ;-)
