# LEDPotato
![image](https://github.com/guysoft/LEDPotato/blob/devel/media/ledpotato.png?raw=true)

A distrubution for Le Potato AML-S905X-CC that controls ws2812 over uart. Right away from boot.

LEDPotato uses [CustomPiOS](https://github.com/guysoft/CustomPiOS) to build the image.

# Donate
LEDPotato is 100% free and open source and maintained by Guy Sheffer. If its helping your life, your organisation or makes you happy, please consider making a donation. It means I can code more and worry less about my balance. Any amount counts. Also many thanks to people contributing code.


[<img src="https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif" alt="Donate button" >](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=26VJ9MSBH3V3W&source=url)

# Where to get it?

The official mirror is [here](https://unofficialpi.org/Distros/LEDPotato)

Nightly builds are available [here](http://unofficialpi.org/Distros/LEDPotato/nightly/) (currently built on demand)

# How to use it?
1. Connect an LED strip to Pin 8 on the Le Potato:
** ADD IMAGES **
2. Unzip the image and install it to an SD card [like any other Le Potato Image](http://wiki.loverpi.com/tutorial:sbc:libre-aml-s905x-getting-started)
3. Boot the Le Potato from the SD card
4. Log into your Le Potato via SSH (it is located at ledpotato.local if your computer supports bonjour or the IP address assigned by your router), default username is "pi", default password is "lepotato" and change the password using the passwd command.
5. You can update the number of leds here:
```
/opt/ledpotato/libretech-saled-light/config/ws2812-uart-gxl-aml6.ini
```
6. You can update the script that controls the leds here:
```
/opt/ledpotato/libretech-saled-light/gen/run_leds.py
```

# Requirements

* Le Potato AML-S905X-CC
* A ws2812 LED strip that is powered independently. I was told to use a Schmitt-Trigger Inverter to handle level shifting, but my led strip works without it.

# Features

* Starts controlling a ws2812 LED strip on boot

# Developing

## Requirements
* qemu-arm-static
* CustomPiOS
* Downloaded Raspbian image.
* root privileges for chroot
* Bash
* realpath
* sudo (the script itself calls it, running as root without sudo won't work)
* jq (part of CustomPiOS dependencies)
* python3-git

# Build LEDPotato From within LEDPotato / Debian / Ubuntu

LEDPotato can be built from Debian, Ubuntu, or even LEDPotato. Build requires about 3.5 GB of free space available. You can build it by issuing the following commands:

```
sudo apt install coreutils p7zip-full qemu-user-static

git clone https://github.com/guysoft/CustomPiOS.git
git clone https://github.com/guysoft/LEDPotato.git

cd FullPageOS/src/image
# Update this to newer images if needed
wget -c --trust-server-names 'https://distro.libre.computer/ci/debian/12/debian-12-base-arm64%2Baml-s905x-cc.img.xz'
cd ..
../../CustomPiOS/src/update-custompios-paths
sudo modprobe loop
sudo bash -x ./build_dist
```

# Building Using Docker

[See Building with docker entry in wiki](https://github.com/guysoft/CustomPiOS/wiki/Building-with-Docker)


# Contribution

Code contribution would be appreciated!
