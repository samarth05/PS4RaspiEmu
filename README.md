# Raspberry Pi Host and USB Emulator for PS4 9.00  

## Local PS4 Jailbreak Host with USB emulation by samarth05
This project is an updated and cleaned downed version of PS4JbEmu by CrazeeGhost with Updated GoldHen and Other Payloads.<br>
It creates a local web host with USB emulation on Raspberry Pi that can be used to Exploit and Jailbreak PS4 consoles running Firmware Version 9.00.<br>
Raspberry Pi Zero W / Pi Zero 2 W / Pi4 B are eligible boards as they support a USB on-the-go (OTG) gadget mode which eliminates the need to Manually Insert and Remove the USB Stick required in the Exploit Process.<br>
This project is implemented on a clean Raspberry Pi OS (Debian) install which makes it easier to repurpose the Pi to run additional applications and services on it.<br>
Developed and Tested on Raspberry Pi Zero W (May work on Other Raspberry Pi's if you follow the Advance Method Mentioned Below).

### Benefits
- Clean Raspberry Pi OS install - Easily Setup Raspberry Pi for any other purposed if required.
- Single device for Local Web Server and USB Emulation
- Does Not Need Any additional USB Drive to Run Exploit. Just Plug it With Single USB to the PS4.
- You can leave the Pi Permanently Connected to the PS4.
- Easily Update Exploit, GoldHen and Payload Files from the Web Interface

### Setup - Auto Method [Pre-Installed Image]
COMING SOON!

### Setup - Manual Method (Requires Basic Linux Command Knowledge)
1. Install a clean Raspberry Pi OS image to an SD card 
[Raspberry Pi OS Lite 32-Bit (Debian Bullseye) Preferred if using Zero W]
2. Enable USB Gadget Mode on the Pi <br>
   a. Add `dtoverlay=dwc2,dr_mode=peripheral` to the `[all]` section inside `/boot/config.txt`
3. Prevent the Pi from automatically becoming a USB gadget on every boot <br />
   a. Add `sudo /sbin/modprobe -r g_mass_storage` to `/etc/rc.local`
5. Install and setup `lighttpd` and `PHP`.<br>
Run : `sudo apt-get install lighttpd` and `sudo apt-get install php`
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
`Update Host` button on the web app will not work if you did not follow the directory strcture in the steps above


Post-Setup Instructions: 
1. After Setting up the Pi for Exploit, connect the Raspberry Pi with USB Cable to PS4 and Make Sure the Cable Supports Data Transfer.<br>
For Raspberry Pi Zero W, plug the Cable to Port marked as 'USB' on the Board.<br>
![image](https://user-images.githubusercontent.com/2664857/149229582-18780783-6d47-4d12-89ab-1898da33e1c7.png)<br/>
2. After Powering Up the PS4, it should Simultaneously Boot up the Pi and Connect the PS4 to the same network as your Raspberry Pi.
3. Go to PS4 Web Browser and type in your Pi's IP Address as below:<br>
http://IP.ADDRESS.OF.PI/ps4 (e.g.: http://192.168.0.0/ps4) and the Exploit Host Page will be opened. It will Cache Some Files and Re-Open The Page Again.
4. Click on GoldHEN Button and a Web Popup will appear showing USB Emulation Started. Wait until the PS4 pop up saying 'This USB Storage device's file system is unsupported' comes and disappeares and Click OK.<br>
![image](https://user-images.githubusercontent.com/20742243/151671687-3a16a6db-a56e-45d8-bc13-9ff76598949d.png)<br/>
5. Then GoldHEN v2.3 will run automatically with BinLoader.
6. Voila! Your PS4 is Exploited Successfully!!


Other Notes:
1. It is recommeded to use Raspberry Pi Imager Tool so you can Set Hostname, Enable SSH, Set Username and Password, Configure Wireless LAN whilst Installing the Raspberry Pi OS to SD Card.
2. For Raspberry Pi Zero W, PHP 7.4 is the easiest to install and it works fine.


### Credits
1.	Sleirsgoevy – Webkit, Offline Activator
2.	Chendochap – KeExploit
3.	Karo Sharifi – Offline Exploit Web Host 
4.	PaulJenkin – Inspiration for USB Emulation
5. CrazeeGhost - PS4JbEmu Files
6. Any Many More...
