# Overview
The Pi Zero W uses modules for it's ethernet or serial information. We currently want the Pi to act as a ethernet device, since we want to connect to it and run code on it remotely.

However, the Pi Zero W can be used as a serial device. This might take some finnageling in the future though.

# Ethernet
In the SD card VIA the SD card reader.
1. open up cmdline.txt
2. After `rootwait`, verify the line says `modules-load=dwc2,g_ether`
3. Verifying the line is g_ether should mean it's goot for ethernet

https://www.catalog.update.microsoft.com/Search.aspx?q=%09Acer%20Incorporated.%20-%20Other%20hardware%20-%20USB%20Ethernet%2FRNDIS%20Gadget
Download Acer Incorporated. - Other hardware - USB Ethernet/RNDIS Gadget	Windows 7, Windows 8, Windows 8.1 and later drivers

Replace the drivers with that.

Boot pi and connect

# Serial / Serial COM
In the SD card VIA the SD card reader.
1. open up cmdline.txt
2. After `rootwait`, verify the line says `modules-load=dwc2,g_serial`
3. Verifying the line is g_serialshould mean it's goot for serial