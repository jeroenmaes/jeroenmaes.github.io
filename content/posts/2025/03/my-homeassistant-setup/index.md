---
title: "My Home Assistant Setup: Hardware, Software, and Automation"
date: "2025-03-12"
categories:   
  - "homeautomation"
tags: 
  - "homeassistant"
  - "raspberry pi"  
---

### **Introduction**  
This page provides a detailed overview of the hardware and software I use to power my smart home. I’ll cover my Raspberry Pi-based hardware setup, the key software add-ons and integrations, the automations I use and some key tips to enhance the security of a typical Home Assistant setup.

### **Hardware**  

- Raspberry Pi 4 (4GB RAM) – The brain of my Home Assistant setup.
- Cooling & Power: Case with heatsinks + Raspberry Pi official USB-C power supply.
- Storage: HP x911w SSD USB 3.2 Stick – Provides better performance and reliability than an SD card.

### **Addons**  

Custom:
- HACS: https://www.hacs.xyz/ - Essential for installing custom integrations and themes.
- Omada Software Controller: https://github.com/jkunczik/home-assistant-omada - Manages TP-Link Omada network devices.
- Cloudflared: https://github.com/brenner-tobias/ha-addons - Secure remote access to Home Assistant via Cloudflare tunnels.

Default:
- Visual Studio Code
- Advanced SSH & Web Terminal


### **Integrations**  

Custom:
- NHC2: https://github.com/joleys/niko-home-control-II
- Jablotron Cloud: https://github.com/Pigotka/ha-cc-jablotron-cloud
- AEG/Elektrolux: ??? for AEG Dryer and Washing machine
- ConnectLife: ??? for Pelgrim Dishwasher

Default:
- Renson for Renson Endura ventilation unit
- Philips Hue
- Bose SoundTouch
- Shelly
- IPP (Internet Printing Protocol) for HP LaserJet Pro
- WLED
- MyUplink for NIBE Heatpump
- SMA Solar

### **Software - Automations**  
- Trigger NHC "Everything Off" action when Jablotron alarm is armed

### **TIPS: **  
- Assign your devices with a static IP or use DHCP address reservation
- Implement GEO restrictions in Cloudflare
- Enable Two-Factor Auth
- Configure backups for HomeAssistant
- Configure backups for Omada Controller
- Use a "Touchscreen profile" with a fixed password in Niko Home Control

---
