# local-intranet
local offline webapps. community intranet!

# Hardware
- Raspberry Pi
- SD Card
- Antenna https://www.newfrog.com/product/outdoor-high-power-wifi-usb-adapter-150mbps-wireless-network-card-signal-receiver-omni-directional-13db-wifi-antenna-802.11b-g-n-117991

# Software

## Install the OS
- Download Raspbian Stretch Lite https://www.raspberrypi.org/downloads/raspbian/
- Flash OS onto the SD Card 
  - Etcher is a great tool https://etcher.io/
  - If on linux you can use dd:
    - df -h to find drive (/dev/sda, /dev/sdb, /dev/sdc, /dev/mmcblk1p
    - sudo umount /dev/sdX1 (for each of the numbered drives, where X is the letter of the drive)
    - sudo dd bs=4 if=your_img_name of=/dev/sdX conv=fsync

## Update and Install Required Packages
- Boot the sd card in the pi. Default login is user:pi, pass:raspberry
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install dnsmasq hostapd
