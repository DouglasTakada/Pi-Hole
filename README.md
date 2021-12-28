# Pi-Hole 2021
This repository is a step by step way I was able to set up my pi hole!

Hello! I am making this repository because I am having to do it again to use a smaller SD card so I thought I might as well document it so it could hopefully help others in the future and in case I have to do it again lol. Although some would consider this project quite simple, becasue it was my first project, it had taken me quite some time simply because of details that were sometimes left out or me questioning doing certain things forunknown reasons. My hope is to create a repo that has everything in one place instead of having to go from one place to another.

## Overview

### my approach
1. Download Operating System onto SD card
2. Configure Raspberry pi using a monitor, mouse and keyboard (won't be covering how to **configure** raspberry pi without monitor, mouse and keyboard)
3. Set up Raspberry Pi next to internet router
4. Download and set up Raspberry Pi through ssh through my main computer
5. Connect Raspberry Pis DNS Server to be the only server that the internet router is connected to
6. Eat beans


### Materials:
 - Seperate computer than the Raspberry Pi
 - Raspberry Pi 
  - SD card
  - SD card Reader
  - Raspberry Pi Case (optional but reccomended if it is set up for long term use)
  - Keyboard (optional)
  - Mouse (optional)
  - Monitor (optional)
 - Ethernet cable (Optional but reccomended if it is set up for long term use)


I would consider this project to have three phases.
### Phase 1 - download OS for Raspberry Pi (set up password/set up VNC/Set up static IP adress)
### Phase 2 - download Pi hole (step by step for each downlaoding page)
### Phase 3 - Connect the Raspberry Pis DNS server to internet router

## Phases

### Phase 1
The very first step is to download the Operating System (OS) to the SD card that will be pluged into the Raspberry Pi to do this you are going to want to download the raspberry pi installer from the **offical** Raspberry Pi website https://www.raspberrypi.com/software/
once it is downloaded open it and choose **Raspberry Pi OS (32-bit)** for the OS and for storage choose the one option that is there and click write and wait for it to download. Once it had completed downloading, take out the SD card and plug it into the Raspberry Pi and everything else you need to plug in to make the Raspberry Pi functioning.
 - Update the Raspberry Pi by entering **sudo apt-get update**
 - Change password by opening the Raspberry pi terminal and typing and entering **passwd**
 - Change the VNC or SSH to turn it on by entering sudo raspi-config and find **Interfacing Options** then turn on VNC or SSH
  - Here is the hard way: https://www.instructables.com/Setting-up-a-VNC-Server-on-your-Raspberry-Pi/
  - Here is the easy way: https://www.realvnc.com/en/connect/
 - Now you are going to want to make your Raspberry Pi adress a static address. to do this you are going to need three things
  1. Raspberry Pi IP adress: use command **hostname -I**
  2. Your Wifi Router IP adress: use command **ip r | grep default** (its the very first IP adress given)
  3. Your current DNS IP adress: use command **sudo nano /etc/resolv.conf** (press **Control X** and press enter to exit the file)
 - Now enter **sudo nano /etc/dhcpcd.conf** and input the following information that you found from the previous commands
-----------------
- interface NETWORK
- static ip_address=STATIC_IP/24
- static routers=ROUTER_IP
- static domain_name_servers=DNS_IP
----------------
 - Once you have entered this into the file exit the file and enter **sudo reboot** to restart to make sure the changes are saved
