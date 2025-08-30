# Update WD Black SN770 Firmware on Linux

## Table of Content

- [Reference](#reference)

Been having problems with my new SN770 drive, and decided to check if I
can firmware update it on Linux. WD only provides a Windows tool,
[Western Digital Dashboard](https://support-en.wd.com/app/products/downloads/softwaredownloads)
to download and install firmwares, but, it's possible to find the
firmware and install it using Linux tooling as well.

## 1. Check that `nvme-cli` is installed:

```bash
❱ sudo pacman -S nvme-cli
```

## 2. Find the current firmware version

Run nvme to check which firmware version is installed:
```bash
❱ sudo nvme id-ctrl /dev/nvme0 | grep "fr "
fr        : 731100WD
```
In my case it tells that firmware is 731100WD.

## 3. Find and download the firmware for your drive

Open the URL that the WD Dashboard Downloads uses, and find your drive
in the list:
https://wddashboarddownloads.wdc.com/wdDashboard/config/devices/lista_devices.xml

My drive was here:

```xml
<lista_device model="WD_BLACK SN770 1TB">
  <url>wdDashboard/firmware/WD_BLACK_SN770_1TB/731120WD/device_properties.xml</url>
</lista_device>
```

From there look at the device_properties.xml,
https://wddashboarddownloads.wdc.com/wdDashboard/firmware/WD_BLACK_SN770_1TB/731120WD/device_properties.xml:

```xml
<ffu version="1.0">
<model>WD_BLACK SN770 1TB</model>
<fwmode>mode3</fwmode>
<fwversion>731120WD</fwversion>
<fwfile>731120WD.fluf</fwfile>
<dependency model="WD_BLACK SN770 1TB">731030WD</dependency>
<dependency model="WD_BLACK SN770 1TB">731100WD</dependency>
</ffu>
```

Now we can download the fluf file:
https://wddashboarddownloads.wdc.com/wdDashboard/firmware/WD_BLACK_SN770_1TB/731120WD/731120WD.fluf

The fluf file is the firmware format for the WD drive. It contains
checksums and drive identifiers, so the drive controller should fail if
you try to install a wrong firmware, but, better double-check that you
have the correct one :-)

## 4. Apply the firmware

Use nvme to download firmware and commit it. Both commands should be
successful.

```bash
❱ sudo nvme fw-download /dev/nvme0 -f ./731120WD.fluf
❱ sudo nvme fw-commit -s 2 -a 3 /dev/nvme0
```

Finally reboot, and step 2 again to check that the firmware is running
on the correct version.

## Reference

* [Update Firmware WD Black SN770 Firmware on Arch Linux](https://gist.github.com/sorend/38aa32b1b07124575026918e5201e299)
