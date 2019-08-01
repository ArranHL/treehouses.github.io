Jul 17, 2018 • [liew211](https://www.github.com/Liew211)  

# Running Nextcloud on Raspberry Pi with Tor

I have recently learned about using Tor to allow a Raspberry Pi to be accessed remotely, and have implemented this with [Nextcloud](https://nextcloud.com/#why-nextcloud).  Nextcloud is a file-storage service similar to Dropbox, but hosted privately from your own Raspberry Pi.  By using Tor to open up the port occupied by Nextcloud, you will be able to access it without needing to be on the same Wifi network, which allows you to use Nextcloud's collaborative features, such as file-sharing and messaging.

### Step 1 - Prepare Treehouses image

Download the latest treehouses image from http://download.treehouses.io, then use [balenaEtcher](https://etcher.io) to flash the image onto your SD card.  Be sure to change balenaEtcher's settings to prevent it from automatically unmounting the SD card once it's done flashing.  

In your file explorer, navigate to the `boot` drive, and open the `autorunonce` file in a text editor of your choice.  Delete everthing, and paste this in:
	
```bash
#!/bin/bash

treehouses rename treehouses
treehouses expandfs
treehouses button bluetooth

treehouses bridge "wifiname" treehouses "wifipassword"

reboot
```
Replace `wifiname` and `wifipassword` with your wifi name and password.  Save the file, and safely eject the SD card.  

### Step 2 - Install the Tor browser on your computer. 

To access the Tor address, you will need to install the Tor browser on your computer.