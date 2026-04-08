<img width="400" height="96" alt="OpenCore_with_text_Small" src="https://github.com/user-attachments/assets/16d50226-0857-4b43-a30c-57b31ca373d6" />

# Lenovo G780 Hackintosh Open Core Config

Open Core config for MacOS Monterey on a Lenovo G780 Laptop
Laptop Specs Intel i7 3720QM CPU  w/ Intel HD4000 Integrated GPU
8GB DDR3
17" 1600x900dpi screen
PS2 Touchpad
2x USB3
2x USB2
DVDRW
Samsung 256GB Sata SSD
Atheros AR8XXX Ethernet (reports 1Gbps, but its a 100Mbps link)

RealTek 802.11ac USB Nic
Lenovo EasyCamera USB Webcam (junk)
Realtek SD Card Reader (registers as built-in)

OpenCore 1.0.6 Debug

# Background
i. 
I built my first hackintosh in 2012, in the days of OSX Mavericks. It was an Ivy bridge i5 3570k, with a Gigabyte GA Z77X up5 TH, with Nvidia GT640, 16GB Ram, and dual booted windows to game. 14 years later and that machine is running MacOS Sequoia, with a de-lidded i7 3770K, with direct to die mounted waterblock, running a daily driver overclock of 4.8ghz (stock speeds are 3.5ghz and 3.9ghz turbo), RX 580 8G, 2TB NVME + 4TB HDD fusion disk, Thunderbolt LAN, Thunderbolt Time Machine, Atheros PCIE wif




## How to use
If your laptop specs match mine, and you've got the same opencore version, you can drag and drop these files into your EFI/EFI/OC Folder, edit the SMBIOS information with your own details, and you should be good to go. 

These laptops came with a variety of Celeron, i3, i5, and i7 processors, and at least one discreet GPU. If your CPU varies from mine - you'll need to generate your own SSDT-PM file to get full working turbo sttes, and cpu power management. 

To check whether your CPU Turbo states are working, download the <a href="https://www.insanelymac.com/forum/files/file/1056-intel-power-gadget/">Intel Power Gadget</a>. note: Intel cancelled this project, and removed all of the downloads from their website - this was the latest version I could find online - I believe you need to be logged in to download. 

## WIFI
Lenovo has some sort of proprietary firmware written to the minipcie wireless card in the machine, which prevents upgrade with a non lenovo card. I'm working on reverse engineering the firmware check to allow non-lenovo wifi cards to be installed. For now I'm using a USB wifi dongle with <a href="https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter">Chris1111's Wifi drivers for Big Sur+</a>.

This driver supports dozens of USB wifi dongles. I've had success with the following: 
TP Link Archer T4Uv3.0 802.11ac USB3 AC1300 Mu-Mimo (RTL8812BU chipset)
TP Link TL-WN722N 150Mbps w/ Detachable 4dBi antenna (R8188EU chipset)
Edimax EW-7811Un 150Mbps "nano" dongle (RTL8188CUS chipset) (consider end of life: won't see wifi routers using modern protocols, doesn't support WPA3)

## The deets
MacBookPro 10,1 SMBIOS for Ivy Bridge platform - dropped in Monterey - requires CryptexFixup, AMFI pass, Skip Board ID Check, and Root patching with Open Core Legacy Patcher. 

It's easiest to use OCLP to generate your Installer USB - It will automatically include some specific packags needed to auto install OCLP during installation, making post install much easier. 

For a full walk through on using OCLP with hackintosh, especially for unsupported CPUs, check out <a href="https://github.com/5T33Z0/OCLP4Hackintosh?tab=readme-ov-file">OCLP4Hackintosh</a>. 

For everything you could want to know about Open Core - I highly recommend <a href="https://github.com/5T33Z0/OCLP4Hackintosh?tab=readme-ov-file">OCLittle Translated</a>

<a href="https://dortania.github.io/OpenCore-Legacy-Patcher/">Open Core Legacy Patcher</a>
This config was started with <a href="https://github.com/lzhoang2801/OpCore-Simplify">OpCore Simplify</a>



Most of the SSDT's and acpi hotpatches generated with <a href="https://github.com/corpnewt/ssdttime">SSDTtime</a>

SSDT-PM generated with <a href="https://github.com/Piker-Alpha/ssdtPRGen.sh">SSDTPRGen</a>










<img width="1600" height="900" alt="Screen Shot 2026-04-08 at 5 19 42 AM" src="https://github.com/user-attachments/assets/e837d5b0-5142-4037-acc5-6762e4a9848d" />
