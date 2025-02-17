---
title: "Breathing New Life into a +10-Year-Old HP N36L MicroServer: My DIY NAS Journey - Part 1"
date: "2025-02-16"
categories: 
  - "nas"
  - "homelab"
tags: 
  - "omv"
  - "hp"
  - "nas"
---

### **Introduction**  
The HP ProLiant MicroServer N36L is a relic of the early 2010s, but with a little ingenuity, it can still serve as a reliable NAS in 2025. In this post, I’ll walk through how I transformed my aging N36L into a modern NAS using cost-effective upgrades and open-source software. Whether you’re a homelab enthusiast or just want to repurpose old hardware, this guide will show you how to squeeze every drop of value from this compact server.  

---

## **1. Updating the BIOS to the Latest Unofficial Version**  
The N36L’s stock BIOS is limited, especially for modern storage configurations. To unlock features like AHCI support (critical for SSD performance) and better hardware compatibility, I flashed an **unofficial BIOS** from the enthusiast community.  

**Steps I followed:**  
- Downloaded the modified BIOS from [Nathaniel Perez](https://www.nathanielperez.us/blog/hp-proliant-n40l-bios-modification-guide).  
- Use a empty USB drive formatted to flash the BIOS using the included utility.
- Read the instructions!  
- Enabled AHCI mode to improve SATA performance and allow hot-swapping drives.  

**⚠️ Warning:** BIOS flashing carries risks. Follow instructions meticulously to avoid bricking your server.  

---

## **2. Upgrading RAM to 8GB for Smoother Performance**  
The N36L’s default 2GB RAM is insufficient for multitasking or running modern NAS software. I upgraded to **8GB DDR3 RAM**.  

**Why 8GB?**  
- **Multitasking:** More RAM allows running Docker containers, VMs, or Plex without hiccups.  

---

## **3. Booting from an Internal USB SSD for Reliability**  
The N36L has a hidden gem: an **internal USB port** perfect for a low-profile boot drive. I opted for the [HP x911w 128GB USB 3.0 SSD](https://www.amazon.com.be/dp/B0B1WSTNBL?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1), which fits snugly inside the chassis.  

**Advantages:**  
- **Durability:** SSDs outlast traditional USB sticks, which often fail under constant read/write cycles.  
- **Neat Installation:** No dangling cables—the drive sits flush in the internal port.  
- **Speed:** While the N36L’s USB 2.0 port limits throughput (~40MB/s), the SSD’s reliability justifies the trade-off.  

---

## **4. Installing OpenMediaVault: The Heart of the NAS**  
OpenMediaVault (OMV) is a lightweight, Debian-based NAS OS ideal for older hardware. Here’s how I set it up:  

**Installation Steps:**  
1. Downloaded the OMV 6.x ISO and flashed it to a USB drive using belenaEtcher.  
2. Boot from the installer USB drive and install OMV to the internal USB SSD.  

**Why OMV?**  
- **User-Friendly:** WebUI simplifies storage, user, and service management.  
- **Extensible:** Plugins add functionality (e.g., SnapRAID, Plex, Tailscale).  
- **Low Overhead:** Runs smoothly on the N36L’s AMD Turion II Neo CPU.  

---

## **5. Installing OMV-Extras and openmediavault-flashmemory**  
Traditional USB sticks fail in a matter of time under constant read/write cycles. The openmediavault-flashmemory plugin tries to overcome that. Even for SSDs this plugin can extend the lifespan.

**Installation Steps:**  
1. Use Putty to connect to the NAS over SSH.
2. Install OMV-Extras 
3. Install the plugin openmediavault-flashmemory via the WebUI

---

## **Conclusion: A Budget NAS That Still Packs a Punch**  
Total cost for this project:  
- **N36L:** Already owned (or ~€50 used).  
- **RAM:** Already owned (or ~€15 new).  
- **USB SSD:** €30.  
- **Drives:** Repurposed from old PCs.  

For under €30, I revived a decade-old server into a functional NAS that handles backups, media streaming, and light homelab duties. While newer builds offer 10GbE and NVMe speeds, the N36L proves that sustainability and affordability can coexist in tech.  

---

## **Further Reading**  
- [HP N36L BIOS Mod Guide](http://microserver.wikidot.com/wiki:n36l-bios-firmwares)  
- [OpenMediaVault Setup Tips](https://www.wundertech.net/diy-nas-build-guide/)  


