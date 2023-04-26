![NexMon logo](https://github.com/seemoo-lab/nexmon/raw/master/gfx/nexmon.png)

# Nexmon Energy Measurement

To measure the energy of the Wi-Fi chip of a Nexus 5 smartphone, we connect the phone according to the
"[Preparation of a Nexus 5 Android Smartphone for Power Analysis](https://www.seemoo.tu-darmstadt.de/assets/images/uploads/nexus5_power_analysis.pdf)"
manual to a [Monsoon Power Monitor](https://www.msoon.com/lvpm-product-documentation). To focus on the 
power consumption in the Wi-Fi chip, we turn off the phones display and let the main processor go into
idle mode. Then the energy consumption is quite constant except of some peaks that show up every 640 
milliseconds. We realized that those peaks can be avoided by turning off the CONFIG_MSM_SMD_PKT 
setting in the kernel, which disables the LTE related hardware. This repository contains the kernel
sources and a .config file we use for our energy consumption experiments.

# How to build the boot.img

1. After cloneing, you need to checkout the kernel branch: `git checkout kernel`
2. Then set some environment variables using: `source setup_env.sh`
3. Dump the existing image with: `sudo -E make dumpboot`. If you used SuperSU the boot.img will be cleaned from files owned by root.
4. Execute `make boot.img` to create a boot.img-file with our patched kernel.
5. Execute `make boot` to reboot the phone into the bootloader and boot the new kernel over adb. Alternatively, you can flash the kernel with `make flash`. The booting process might take longer than with the regular kernel.

# Contact

* [Matthias Schulz](https://seemoo.tu-darmstadt.de/mschulz) <mschulz@seemoo.tu-darmstadt.de>

# Powered By

## Secure Mobile Networking Lab (SEEMOO)
<a href="https://www.seemoo.tu-darmstadt.de">![SEEMOO logo](https://github.com/seemoo-lab/nexmon/raw/master/gfx/seemoo.png)</a>
## Networked Infrastructureless Cooperation for Emergency Response (NICER)
<a href="https://www.nicer.tu-darmstadt.de">![NICER logo](https://github.com/seemoo-lab/nexmon/raw/master/gfx/nicer.png)</a>
## Multi-Mechanisms Adaptation for the Future Internet (MAKI)
<a href="http://www.maki.tu-darmstadt.de/">![MAKI logo](https://github.com/seemoo-lab/nexmon/raw/master/gfx/maki.png)</a>
