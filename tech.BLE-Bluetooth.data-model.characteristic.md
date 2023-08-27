---
id: xsvu5covaj0m156oxe23wir
title: characteristic
desc: ''
updated: 1690164570399
created: 1690164426601
---

## Bluetooth Characteristic:

1. **Definition**: A Characteristic is a data value used within a Service. It provides further details about the nature and structure of the data within that Service. For instance, within the "Heart Rate Service", there might be a "Heart Rate Measurement Characteristic" which provides the actual BPM (beats per minute) value.

2. **Role**: Characteristics are used to define the data you're either pushing to a device or pulling from a device. They can be read, written to, or can notify a connected device of its changes.

3. **Properties**: Characteristics have properties that define how their value can be accessed (e.g., read, write, notify).

   - **Read**: The value can be read.
   - **Write**: The value can be updated.
   - **Notify**: The peripheral (server) can notify the central (client) of changes to the value without being asked.

4. **Descriptors**: These are secondary, optional attributes that describe the characteristics' value or allow the client to configure how the server behaves. For instance, a Descriptor might allow a device to enable or disable notifications for a particular characteristic.

5. **Identification**: Like Services, Characteristics also have UUIDs. There are common UUIDs standardized by the Bluetooth SIG, but custom ones can be created for proprietary purposes.
