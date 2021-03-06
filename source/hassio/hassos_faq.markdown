---
title: "Home Assistant OS FAQ"
description: "Frequently Asked Questions for Home Assistant OS"
---
## Is USB Boot for the Pi4 supported? Is the Pi4 with 8GB RAM supported?

The bootloader for Home Assistant OS (uboot) does not yet support Pi4 booting from USB. Support is likely a month or two away as of July 2020.

The Pi4 with 8GB RAM is similarly waiting for support from upstream.

## How do I run a specific version of Home Assistant?

For this you would need to install the [Terminal & SSH add-on][ssh] or use the console
that is available on your device by connecting a keyboard and screen.

To install the Terminal & SSH add-on, choose **Supervisor**, which is located in the sidebar and then the add-on store. If you don't see it, enable "Advanced Mode" from your profile page.

Use the web-based terminal or SSH to your Home Assistant system, or connect to the console, and run:

```bash
ha core update --version=0.XX.X
```

Replace 0.XX.X with the version you want. e.g., `0.111.2`

You can also use a similar command for the operating system:

```bash
ha os update --version 4.11
```

## Do I need to leave the USB stick connected for Wi-Fi?

No. The USB "CONFIG" stick is only used to import a network profile to `/etc/NetworkManager/system-connections/` and can be removed.

## 404 Client Error: Not Found ("no such image: homeassistant/...)

This error indicates the image, whether for updating to Home Assistant or installing or updating an add-on, was not able to be pulled to your system. This is usually a situation where there is not enough space for the image to be downloaded. The first thing to check for is the available space on your system.

Please note, if you are running the operating system as a virtual machine; the default VM image is only about 6GB. Many VM users run into this as they have not allocated enough storage. 32GB is the minimum recommended size.

You will need to explore your own system to determine where space has gone.
Using `df -h` in the SSH add-on console to you can quickly check to see if you have space available.

If there is plenty of space available then you might check to see if you are having network issues that are preventing images from being downloaded.

## Why does the start button for an add-on flash red when I click it?

If you are looking for more information about add-ons, which won't start or install, navigate to Supervisor > System in the UI and check the logs.

The logs on this page are the same you would see using `ha logs` in the custom CLI.

## I'm trying to find my files on the host or SD card. Where are they?

On a Home Assistant OS install, your files are on the data partition within `/mnt/data/supervisor/`.
On the SD itself, this is an EXT4 partition labeled `hassos-data`.

On a Supervised install, they are in `/usr/share/hassio/`.
