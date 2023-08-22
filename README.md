# Raspberry Pi Emulator for PS4 9.00  

## Local PS4 Jailbreak Host with USB emulation by samarth05
This project is an updated and cleaned downed version of PS4JbEmu by CrazeeGhost with Updated GoldHen and Other Payloads.<br>
It creates a local web host with USB emulation on Raspberry Pi that can be used to Exploit and Jailbreak PS4 consoles running Firmware Version 9.00.<br>
Raspberry Pi Zero W / Pi Zero 2 W / Pi4 B are eligible boards as they support a USB on-the-go (OTG) gadget mode which eliminates the need to Manually Insert and Remove the USB Stick required in the Exploit Process.<br>
This project is implemented on a clean Raspberry Pi OS (Debian) install which makes it easier to Repurpose the Pi to Run Additional Applications and Services on it.<br>
Developed and Tested on Raspberry Pi Zero W (May work on Other Raspberry Pi's if you follow the Manual Method Mentioned Below).

### Benefits
- Clean Raspberry Pi OS install - Easily Setup Raspberry Pi for Any Other Purposes if Required.
- Single device for Local Web Server and USB Emulation
- Does Not Need Any Additional USB Drive to Run Exploit. Just Plug it With Single USB to the PS4.
- You can leave the Pi Permanently Connected to the PS4.
- Easily Update Exploit, GoldHen and Payload Files from the Web Interface

### Setup - Easy Method
COMING SOON!!

### Setup - Advanced Method
1. Install a clean Raspberry Pi OS image to an SD card 
[Raspberry Pi OS Lite 32-Bit (Debian Bullseye) Preferred if using Zero W]
2. Enable USB Gadget Mode on the Pi <br>
   a. Add `dtoverlay=dwc2,dr_mode=peripheral` to the `[all]` section inside `/boot/config.txt`
3. Prevent the Pi from automatically becoming a USB gadget on every boot <br />
   a. Add `sudo /sbin/modprobe -r g_mass_storage` to `/etc/rc.local`
5. Install and setup `lighttpd` and `PHP` (PHP 7.4 Works Good on Zero W)
6. Configure `/var/www/html/ps4` as the document root directory for the exploit app (via `lighttpd` configs)
7. Clone or download the source code from this repo <br>
   a. `cd /home/pi` <br>
   b. `sudo git clone https://github.com/samarth05/PS4RaspiEmu.git` <br />
   c. `sudo git config --global --add safe.directory /home/pi/PS4RaspiEmu`
8. Allow the webserver user to run some commands as root without password <br>
   a. Add `www-data ALL = NOPASSWD: /sbin/modprobe, /sbin/reboot, /sbin/shutdown, /var/www/html/ps4/updateHost.sh` to your `sudoers` file using the `visudo` command
9. Make the web app accessible to the webserver <br />
   a. `sudo chmod 755 /home/pi/PS4RaspiEmu/updateHost.sh` <br />
   b. `sudo /home/pi/PS4RaspiEmu/updateHost.sh`


Note: 
1. While Connecting to Raspberry Pi Zero W, make sure the USB cable Supports Data Transfer and plug the Cable to Port marked as 'USB' on the Raspberry Pi Board.

2. `Update Host` button on the web app will not work if you did not follow the directory strcture in the steps above

### Credits
1.	Sleirsgoevy – Webkit, Offline Activator
2.	Chendochap – KeExploit
3.	Karo Sharifi – Offline Exploit Web Host 
4.	PaulJenkin – Inspiration for USB Emulation
5.      CrazeeGhost - PS4JbEmu Files
6.      Any Many More...
