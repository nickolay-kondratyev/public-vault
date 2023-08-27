---
id: kv4qkd4ua75yrdo4xi49739
title: Bluetooth peripheral
desc: ''
updated: 1690166012822
created: 1690165979142
---


In the context of Bluetooth Low Energy (BLE), the term "peripheral" refers to a device that advertises its presence and offers services that a central device can connect to. The peripheral typically provides data and services, and the central reads from or writes to the peripheral.

Here's a more detailed breakdown:

1. **Peripheral Device**:
   - **Role**: Acts as a server. 
   - **Responsibility**: Advertises its availability and provides services and characteristics that a central can access.
   - **Typical Examples**: Wearable devices (like fitness trackers), sensors, beacons, and other low-power devices.

2. **Central Device**:
   - **Role**: Acts as a client.
   - **Responsibility**: Scans for available peripherals, initiates connections, and reads/writes data from/to peripherals.
   - **Typical Examples**: Smartphones, tablets, or computers.

In many BLE interactions, the peripheral offers the data (like a heart rate from a fitness tracker) and the central reads that data. The peripheral can also receive commands or data from the central, such as configuration commands or control signals.