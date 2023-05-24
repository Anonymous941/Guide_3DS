---
title: "Installing boot9strap (Fredtool, Legacy)"
---

{% include toc title="Table of Contents" %}

{% capture technical_info %}
<summary><em>Technical Details (optional)</em></summary>

To dump system DSiWare, we exploit a flaw in the DSiWare Data Management window of the Settings application.

To accomplish this, we use your system's encryption key (movable.sed) to build a DSiWare backup that exploits the system to dump the DSi Internet Settings application to the SD root.

Once we have a DSiWare backup, we can inject it into the DS Internet Settings application.

This is a currently working implementation of the "FIRM partitions known-plaintext" exploit detailed [here](https://www.3dbrew.org/wiki/3DS_System_Flaws).

{% endcapture %}
<details>{{ technical_info | markdownify }}</details>
{: .notice--info}

You should only be able to get to this page if you are running version 11.15.0 or 11.14.0. If you are on any firmware other than 11.15.0 or 11.14.0, STOP as these instructions WILL LEAD TO A BRICK on other firmwares!!
{: .notice--warning}

### What You Need

* Your `movable.sed` file from completing [Seedminer (Mii)](seedminer-(mii))
* The latest release of [Frogminer_save](https://github.com/zoogie/Frogminer/releases/latest) (`Frogminer_save.zip`)
* **11.15.0 and 11.14.0 users only**: The v6.0.1 release of [b9sTool](https://github.com/zoogie/b9sTool/releases/tag/v6.0.1) (direct download)
* The latest release of [Luma3DS](https://github.com/LumaTeam/Luma3DS/releases/latest) (the Luma3DS `.zip` file)

#### Section I - CFW Check

{% include_relative include/cfw-check-fredtool.txt %}

#### Section II - BannerBomb3

In this section, you will trigger the BannerBomb3 exploit using the DSiWare Management menu and copy the resulting file dump to your computer so that you can use it on the next section.

1. Reinsert your SD card into your device
1. Power on your device
1. Launch System Settings on your device
1. Navigate to `Data Management` -> `DSiWare`-> `SD Card` ([image](/images/screenshots/bb3/dsiware-management.png))
  + Your device should show the BB3 multihax menu
  + If this step causes your device to crash, [follow this troubleshooting guide](troubleshooting#installing-boot9strap-fredtool)
1. Use the D-Pad to navigate and press the (A) button to select "Dump DSiWare"
  + Your device will automatically reboot
1. Power off your device
  
#### Section III - Prep Work

{% include_relative include/fredtool-prep.md %}

#### Section IV - Overwriting DS Connection Settings

{% include_relative include/fredtool-write-flipnote.md %}

#### Section V - Flipnote Exploit

{% include_relative include/install-boot9strap-b9stool.txt method="dsinternet" %}

#### Section VI - Luma3DS Configuration

1. Press and hold (Select), and while holding (Select), power on your device. This will launch Luma3DS configuration
{% include_relative include/configure-luma3ds.txt %}

{% include_relative include/luma3ds-installed-note.txt %}

#### Section VII - Restoring DS Connection Settings

{% include_relative include/fredtool-restore-dsconn.md %}

___


### Continue to [Finalizing Setup](finalizing-setup)
{: .notice--primary}