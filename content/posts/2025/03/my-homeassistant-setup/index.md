---
title: "My Home Assistant Setup"
date: "2025-03-12"
categories:   
  - "homeautomation"
tags: 
  - "homeassistant"
  - "raspberry pi"  
---

### **Introduction**  
This page gives an overview of my Home Assistant setup: the hardware and the software.

### **Hardware**  

- Raspberry Pi 4 4GB
- Case + Heatsinks
- Raspberry Pi official USB-C power supply
- HP x911w SSD USB3.2 Stick

### **Software - Addons**  

Custom:
- HACS: https://www.hacs.xyz/
- Omada Software Controller: https://github.com/jkunczik/home-assistant-omada
- Cloudflared: https://github.com/brenner-tobias/ha-addons

Default:
- Visual Studio Code
- Advanced SSH & Web Terminal


### **Software - Integrations**  

Custom:
- NHC2: https://github.com/joleys/niko-home-control-II
- Jablotron Cloud: https://github.com/Pigotka/ha-cc-jablotron-cloud

Default:
- Renson
- Philips Hue
- Bose SoundTouch
- Shelly
- IPP (Internet Printing Protocol) for my HP LaserJet Pro
- WLED

### **Software - Automations**  
- Trigger NHC "Everything Off" action when Jablotron alarm is armed

### **BONUS: Tips**  
- Assign your devices with a static IP or use DHCP address reservation
- Configure backups for HomeAssistant
- Configure backups for Omada Controller

---
