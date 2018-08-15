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
  - SSH can be enabled by placing a file named 'ssh', without any extension, onto the boot partition of the SD card
  - Setup wifi to be able to ssh into the pi immediately
    - Add file named wpa_supplicant.conf to the boot partition with the following contents (inserting your network info)
      ```
      ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
      network={
          ssid="YOUR_NETWORK_NAME"
          psk="YOUR_PASSWORD"
          key_mgmt=WPA-PSK
      }
      ```

## Update and Install Required Packages
- Boot the sd card in the pi. Default login is user:pi, pass:raspberry
- sudo raspi-config
  - Change User Password
  - Localisation Options - Change Keyboard Layout - Generic 104-key PC - Other - English (US) - Default Keyboard Layout - No Compose Key
  - Network Options - Wifi - Enter SSID and Password (if not setup already)
  - Interfacing Options - SSH - Enable (if not setup already)
  
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install dnsmasq hostapd
- sudo systemctl stop dnsmasq
- sudo systemctl stop hostapd
- sudo cp /etc/dhcpcd.conf /etc/dhcpcd.conf.bak
- sudo nano /etc/dhcpcd.conf

## Troubleshooting
### Changing Wifi Password
 - sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
 - modify contents, Ctrl+X to close
 - sudo reboot
