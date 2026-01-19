---
title: "Adding Matter over Thread to my Home Assistant setup"
date: 2026-01-19
description: "How I added Matter over Thread to Home Assistant using a Sonoff ZBDongle-E."
tags:
  - home-assistant
  - matter
  - thread
  - smart-home
---

I wanted to start using **Matter** devices in my Home Assistant setup. More specific the new IKEA TIMMERFLOTTE, a very affordable temperature monitor. 
Matter itself is the interoperability layer (the universal languange), while **Thread** is a low-power mesh protocol. 

This post is the quick checklist I followed to get everything working.

## Step 1: Buy the correct dongle — Sonoff ZBDongle-E

To add Thread support to Home Assistant, you’ll typically need a compatible USB radio dongle. I went with the **Sonoff ZBDongle-E**.

Why this one:

- widely used in the Home Assistant community
- solid Thread support once flashed with the right firmware
- easy to plug into my Raspberry Pi
- dual radio that supports in theory both Zigbee and Thread (not tested for now)

## Step 2: Flash the firmware 

Before Home Assistant can use the dongle for Thread, it needs the right firmware.

I used the **SONOFF Dongle Flasher** addon, which makes this part much simpler than doing it from another machine.

High-level flow:

1. Install the flasher add-on.
2. Select the correct USB device (double-check you’re flashing the Sonoff dongle).
3. Pick the recommended Thread-capable firmware for the ZBDongle-E.
4. Flash and reboot if needed.

## Step 3: Install the OpenThread Border Router

Next up: Thread itself.

In Home Assistant, install the **OpenThread Border Router** addon and configure it to use the flashed Sonoff dongle as the radio interface. Once it’s running, you should be able to see Thread becoming available as an integration/feature in your setup.

At this point you’re basically creating a Thread network that Matter devices can use.

## Step 4: Install the Matter Server

With Thread running, I installed the **Matter Server**.

The Matter Server is what lets Home Assistant talk the Matter protocol and actually pair/control Matter devices. After installing it:

- start the add-on
- confirm Home Assistant detects it (Integration should appear or be discoverable)
- keep it running permanently (pairing and device control depend on it)

Once this is in place, you can start pairing Matter devices via Home Assistant.

## Step 5: Extend the network range with a better antenna and the Aqara M100 hub

I first started by replacing the default antenna with a larger one that I had lying around from an old donor WIFI router, but this was not sufficient in my case.

Thread is a mesh network, so coverage can be expanded with additional Thread-capable routers/border devices. To improve range and stability, I extended my Thread coverage using the **Aqara Hub M100**.
You need the Aqara smartphone app to link the device to your WIFI network. Once configured it will be able to join the existing Thread network.

This helped in parts of the house where devices were a bit far from the Home Assistant host + dongle.

---

That’s it: dongle, firmware, Thread, Matter Server, and then better coverage. Next up for me is adding a few more Matter-over-Thread devices and seeing how reliable it stays over time.
