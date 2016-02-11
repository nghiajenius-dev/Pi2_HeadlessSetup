# Pi2_HeadlessSetup

Setup Raspberry Pi 2 without HDMI display or keyboard - Headless Setup

In this tutorial, I will show you how to:
- Create Bootable Linux Image
- Remote Acess Raspberry Pi via SSH
- Initial Configuration
- Remote Desktop via VNC Server on Mac

## Create bootable Linux Image

There is a detail instruction in [Raspberry Pi Official Site](https://www.raspberrypi.org/documentation/installation/installing-images/), 
but I want to cover the step heres so that you don't need to jump back and forth.

There are lots of Linux distro to choose, but I recommend [Raspbian](https://www.raspberrypi.org/downloads/raspbian/)
because it has a good support from community.
[NOOBS](https://www.raspberrypi.org/downloads/noobs/) is an installer for Raspbian, 
and it requires a real display and keyboard to work.

In this tutorial, I assume that you don't have anything except a Pi and a Mac, 
so you need to create a bootable Raspbian right on your SD Card.

First, you need to download a suitable Linux image for Raspberry [here](https://www.raspberrypi.org/downloads/).
There will be 2 versions of Raspbian: Jessie (kernel 4) and Wheezy (kernel 3). 
I choose [Raspbian Jessie](https://downloads.raspberrypi.org/raspbian_latest) to install.
After downloaded, unzip the file to get **.img** Linux image, such as ```2016-02-09-raspbian-jessie.img_```

Second, you have to format your microSD Card using [SDFormatter](https://www.sdcard.org/downloads/formatter_4/)
You can choose ```Quick Format``` if you dont want to wait, it will work just fine.

Now, before writing Raspbian image to your SD Card, we need to locate your image directory and the SD Card disk on file system.
- If you choose default option, your Linux image should be in ```Downloads``` folder on your Mac.
- Open **Terminal** Application, run:
```diskutil list```
- You will recognize you SD Card by its name and capacity. In my case it is ```disk2```
- Now run dis command to start writing your linux image to SD Card, **be careful** with the details if you don't want to wipe out a wrong disk.
```bash
 sudo dd bs=1m if=image.img of=/dev/rdisk<disk# from diskutil>
```
Eg: ```sudo dd bs=1m if=/Users/NghiaJenius/Downloads/2016-02-09-raspbian-jessie.img of=/dev/rdisk2```
If you got problem, check the details [here](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md).

Prompt your password for admin right, and wait about 15 mins. 
Now, you are ready to boot up for Raspberry Pi.







