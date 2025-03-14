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
This page provides a detailed overview of the hardware and software I use to power my smart home. I’ll cover my Raspberry Pi-based hardware setup, the key software add-ons and integrations, the automations I use and some key tips to enhance the security of a typical Home Assistant setup.

### **Hardware**  

- **Raspberry Pi 4 (4GB RAM)** – The brain of my Home Assistant setup.
- **Cooling & Power** - Simple 3D printed case with some aluminium heatsinks + Raspberry Pi official USB-C power supply.
- **Storage: HP x911w SSD USB 3.2 Stick** – Provides better performance and reliability than an SD card.

### **Addons**  

Custom:
- **[HACS (Home Assistant Community Store)](https://www.hacs.xyz/):** Essential for installing custom integrations and themes.
- **[Omada Software Controller](https://github.com/jkunczik/home-assistant-omada):** Manages TP-Link Omada network devices.
- **[Cloudflared](https://github.com/brenner-tobias/ha-addons):** Secure remote access to Home Assistant via Cloudflare tunnels.

Default:
- **Visual Studio Code** - Built-in editor for managing Home Assistant configuration.
- **Advanced SSH & Web Terminal** - Provides full SSH access for troubleshooting and automation.


### **Integrations**  

Custom:
- **[NHC2](https://github.com/joleys/niko-home-control-II):** Integration for Niko Home Control II domotica system.
- **[Jablotron Cloud](https://github.com/Pigotka/ha-cc-jablotron-cloud):** Connects Jablotron security systems.
- **[Home Assistant Electrolux Status](https://github.com/albaintor/homeassistant_electrolux_status)**: Integration for AEG Dryer and Washing machine.
- **[ConnectLife](https://github.com/oyvindwe/connectlife-ha)**: Integration for Pelgrim Dishwasher.

Default:
- Renson for Renson Endura ventilation unit
- Philips Hue for Lights
- Bose SoundTouch for Audio controll
- Shelly for Power monitoring
- IPP (Internet Printing Protocol) for HP LaserJet Pro
- WLED for LED controll
- MyUplink for NIBE Heatpump
- SMA Solar for Solar power monitoring

### **Automations**  
- **Trigger "Everything Off"** – When the Jablotron alarm is armed, turns off all Niko Home Control lights and smart outlets by calling the "Everything Off" action using the NHC2 AddOn.


### **Security & Optimization Tips**  
- Assign your devices with a static IP or use DHCP address reservation
- Implement GEO restrictions in Cloudflare for your Tunnel
- Enable Two-Factor Auth for HomeAssitant login
- Configure automated backups for HomeAssistant and the Omada Controller
- Store your backups on a different location and not the storage of you HomeAssistant server itself
- Use a "Touchscreen profile" with a fixed password in Niko Home Control so you don't need to update the token every year

---
