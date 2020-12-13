# headless_raspberry_setup

## Table of Content
1. [ General ](#general) <br/>
2. [ Supported Platforms ](#supported_platforms) <br/>
3. [ Setup Process [wifi] ](#setup_process_wifi) <br/>
4. [ Setup Process [usb] ](#setup_process_usb) <br/>

---
<a name="general"></a>
## General
This repository was created as a quick reference page for Raspberry Pi Setup without keyboard and/or monitor. <br/>
Raspberry Pi Lite image was used for a fast test system setup, due to it's size process should be take more than an afternoon tea break. <br/>

---
<a name="supported_platforms"></a>
## Supported Platforms
Tested on Raspberry Pi Zero, process should suit rest of Raspberries. <br/>



---
<a name="setup_process_wifi"></a>
## Raspberry Setup [wifi]
0. Erase and Format SD Card. <br/>
1. Burn an OS image using Balena Etcher. <br/>
2. Reinsert SD Card into PC.
3. Open SD Card as a Drive. <br/>
4. In Root: <br/>
4.1. Enable ssh by creating empty ssh file. <br/>
4.2. Create a file: wpa_supplicant.conf, which contains: <br/>
&emsp;country=US <br/>
&emsp;ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev <br/>
&emsp;update_config=1 <br/>
&emsp;network={ <br/>
&emsp;ssid="WIFI_SSID" <br/>
&emsp;scan_ssid=1 <br/>
&emsp;psk="WIFI_PASSWORD" <br/>
&emsp;key_mgmt=WPA-PSK <br/>
&emsp;} <br/>
5. Eject SD Card. <br/>
6. Insert SD Card into Raspberry and power it up. <br/>
7. Ssh into it by ssh pi@raspberrypi.local command. <br/>

---
<a name="setup_process_usb"></a>
## Raspberry Setup [usb]
0. Erase and Format SD Card. <br/>
1. Burn an OS image using Balena Etcher. <br/>
2. Reinsert SD Card into PC.
3. Open SD Card as a Drive. <br/>
4. In Root: <br/>
4.1. Enable ssh by creating empty ssh file. <br/>
4.2. Modify cmdline.txt. insert modules-load=dwc2,g_ether between rootwait and quiet. <br/>
4.3. Modify config.txt. append dtoverlay=dwc2 to the eof. <br/>
5. Eject SD Card. <br/>
6. Insert SD Card into Raspberry and power it up. <br/>
7. Connect Raspberry to PC via signal cable. <br/>
8. Raspberry should be found in "Network Connections". <br/>
9. Ssh into it by ssh pi@raspberrypi.local command. <br/>

---