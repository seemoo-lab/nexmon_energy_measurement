# Nexmon Energy Measurement

To measure the energy of the Wi-Fi chip of a Nexus 5 smartphone, we connect the phone according to the
"[Preparation of a Nexus 5 Android Smartphone for Power Analysis](https://www.seemoo.tu-darmstadt.de/fileadmin/user_upload/Group_SEEMOO/mschulz/nexus5_power_analysis.pdf)"
manual to a [Monsoon Power Monitor](https://www.msoon.com/LabEquipment/PowerMonitor/). To focus on the 
power consumption in the Wi-Fi chip, we turn off the phones display and let the main processor go into
idle mode. Then the energy consumption is quite constant except of some peaks that show up every 640 
milliseconds. We realized that those peaks can be avoided by turning off the CONFIG_MSM_SMD_PKT 
setting in the kernel, which disables the LTE related hardware. This repository contains the kernel
sources and a .config file we use for our energy consumption experiments.

# How to build the boot.img

1. After cloneing, you need to checkout the kernel branch: `git checkout kernel`
2. Then you need to set some environment variables using: `source setup_env.sh`
