# headless_raspberry_setup

## Table of Content

1. [ General ](#general) <br/>
2. [ Supported Platforms ](#supported_platforms) <br/>
3. [ Operaion System Setup ](#setup_process_os) <br/>
3.1. [ Resources ](#resources) <br/>
3.2. [ Flash OS ](#flash_os) <br/>
4. [ Setup Process [wifi] ](#setup_process_wifi) <br/>
5. [ Setup Process [usb] ](#setup_process_usb) <br/>

---
<a name="general"></a>
## 1. General

This repository was created as a quick reference page for Raspberry Pi Setup without keyboard and/or monitor. <br/>
Raspberry Pi Lite image was used for a fast test system setup, due to it's size process should be take more than an afternoon tea break. <br/>

---
<a name="supported_platforms"></a>
## 2. Supported Platforms

Tested on Raspberry Pi Zero, process should suit rest of Raspberries. <br/>

---
<a name=setup_process_os></a>
## 3. OS Setup

This paragraph will describe steps to setup Rasspberry pi with OS. <br/> 
Please complete this common section and follow with wifi or usb setups from following chapters. <br/>

<a name="resources"></a>
### 3.1 Resources
Fresh OS image:
[ raspberry os ](https://www.raspberrypi.org/software/operating-systems/) <br/>

Image Flash application:
[ balena etcher ](https://www.balena.io/etcher/) <br/>

<a name="flash_os"></a>
### 3.2 Load OS
0. Erase and Format SD Card. <br/>
1. Burn an OS image using Balena Etcher. <br/>
2. Reinsert SD Card into PC.
3. Open SD Card as a Drive. <br/>

That navigated to /root <br/>
Follow Raspberry Setups for Wifi or USB. <br/>

---
<a name="setup_process_wifi"></a>
## 4. Raspberry Setup [wifi]

1. In Root: <br/>
1.1. Enable ssh by creating empty ssh file. <br/>
1.2. Create a file: wpa_supplicant.conf, which contains: <br/>
&emsp;country=US <br/>
&emsp;ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev <br/>
&emsp;update_config=1 <br/>
&emsp;network={ <br/>
&emsp;ssid="WIFI_SSID" <br/>
&emsp;scan_ssid=1 <br/>
&emsp;psk="WIFI_PASSWORD" <br/>
&emsp;key_mgmt=WPA-PSK <br/>
&emsp;} <br/>
2. Eject SD Card. <br/>
3. Insert SD Card into Raspberry and power it up. <br/>
4. Ssh into it by ssh pi@raspberrypi.local command. <br/>

---
<a name="setup_process_usb"></a>
## 5. Raspberry Setup [usb]

1. In Root: <br/>
1.1. Enable ssh by creating empty ssh file. <br/>
1.2. Modify cmdline.txt. insert modules-load=dwc2,g_ether between rootwait and quiet. <br/>
1.3. Modify config.txt. append dtoverlay=dwc2 to the eof. <br/>
2. Eject SD Card. <br/>
3. Insert SD Card into Raspberry and power it up. <br/>
4. Connect Raspberry to PC via signal cable. <br/>
5. Raspberry should be found in "Network Connections". <br/>
6. Ssh into it by ssh pi@raspberrypi.local command. <br/>

---