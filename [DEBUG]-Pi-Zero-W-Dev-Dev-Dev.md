# Pi Zero W Development Envrionment Setup
Original Author: Zach Kangas

In this I will attempt to create a 'Dev environment setup crash course'.


# Prereqs
## Programs

### CLion 
While I don't want to make this a hard requirement, it's free for us students and supports WSL out of the box. So, sucks to suck unless someone else wants to figure out how to not use it. It's fairly similar to the other JetBrains IDEs, so if you've used those (PyCharm, IntelliJ, Rider, etc), you will be familiar with this.

### ~~Putty~~ May not be necessary

### Debain WSL
Search "Debian" in microsoft store

## Drivers
### Bonjour // This MAY be unnecessary. Worth it to include
https://support.apple.com/kb/dl999?locale=en_US

### USB Ethernet / RNDIS Driver
https://www.catalog.update.microsoft.com/Search.aspx?q=%09Acer%20Incorporated.%20-%20Other%20hardware%20-%20USB%20Ethernet%2FRNDIS%20Gadget

# Guide
## Setup Windows
This is mostly a tertiary step. Grab CLion, Debian (through microsoft store), Bonjour, and the usb drivers above.
### Verify you can ssh into the Pi
1. Open Windows Powershell
2. Type `ssh oled@oledpi.local`
3. If a prompt comes up asked about security bla bla, type yes or y
4. The password is `pi`
5. Are you in? If not... working on it :)


## Setup WSL

This section will take you through setting up your debian instance. This will take a while AND require you have the raspberry pi connected.

This is **heavily** based on the following: https://github.com/abhiTronix/raspberry-pi-cross-compilers/wiki/Cross-Compiler-CMake-Usage-Guide-with-rsynced-Raspberry-Pi-32-bit-OS#cross-compiler-cmake-usage-guide-with-rsynced-raspberry-pi-32-bit-os

1. Install Debian
- This can be done through the microsoft store
2. Update Debian and install necessary packages
```
sudo apt update
sudo apt dist-upgrade
sudo apt install build-essential cmake unzip gfortran
sudo apt install gcc git bison python gperf pkg-config gdb-multiarch wget rsync
sudo apt install g++ gperf flex texinfo gawk bison openssl pigz libncurses-dev autoconf automake tar figlet wget
```
4. Download the toolchain
```
wget https://sourceforge.net/projects/raspberry-pi-cross-compilers/files/Raspberry%20Pi%20GCC%20Cross-Compiler%20Toolchains/Bullseye/GCC%2010.3.0/Raspberry%20Pi%201%2C%20Zero/cross-gcc-10.3.0-pi_0-1.tar.gz
```
5. Extract the toolchain
```
tar xf cross-gcc-10.3.0-pi_0-1.tar.gz
```
6. Setup a directory in root
```
sudo mkdir /rpi_rootfs
```
7. Rsync with the PI - ***This requires you have the pi connected and working***

DM me if it isnt working
```
sudo rsync -avz --rsync-path="sudo rsync" --delete oled@oledpi.local:/lib /rpi_rootfs/
sudo rsync -avz --rsync-path="sudo rsync" --delete oled@oledpi.local:/usr/include /rpi_rootfs/usr
sudo rsync -avz --rsync-path="sudo rsync" --delete oled@oledpi.local:/usr/lib /rpi_rootfs/usr
sudo rsync -avz --rsync-path="sudo rsync" --delete oled@oledpi.local:/opt/vc /rpi_rootfs/opt
```

8. Fix Symbolic Links
```
wget https://raw.githubusercontent.com/abhiTronix/rpi_rootfs/master/scripts/sysroot-relativelinks.py
```
```
sudo chmod +x sysroot-relativelinks.py
sudo ./sysroot-relativelinks.py /rpi_rootfs
```

## Setup Development Environment in CLion
TODO

