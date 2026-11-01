---
title: "usbkit API contracts"
summary: "Platform support, result semantics, and operational constraints for usbkit."
category: "Reference"
order: 20
keywords: ["usbkit", "USBKit", "native", "discovery"]
symbols: ["USBDeviceInfo", "USBDevices", "USBDiscoverySupported", "USBDiscoveryAvailable"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# usbkit API contracts

## Platform support

| Target | Backend | Availability probe |
| --- | --- | --- |
| Linux | USB sysfs | Opens and closes /sys/bus/usb/devices |
| Windows | SetupAPI USB enumerator | Probes SetupAPI and kernel32 |
| macOS | Unsupported | Returns False |

Availability is a probe rather than a guarantee that enumeration will succeed. The probe does not enumerate devices.

## Snapshot fields

`USBDeviceInfo` contains read-only owned values. `Id` is a sysfs device name on Linux or a PnP instance ID on Windows. It is not an open device handle or a cross-platform stable identity.

| Field | Linux | Windows |
| --- | --- | --- |
| VendorId, ProductId | Present numeric IDs | Parsed from VID_/PID_ in the instance ID when present |
| BusNumber, DeviceNumber | Present topology values | None |
| Name | Optional product text | Optional SetupAPI name |
| Manufacturer | Optional text | Optional SetupAPI text |
| Product, SerialNumber | Optional sysfs text | None |

Absent values are `None`; a present empty string is `Some("")`. Do not replace missing numeric fields with zero. Topology numbers can change after reconnecting a device.

## Results and errors

An empty array means successful enumeration with no devices. Native failures, missing libraries, and inaccessible discovery resources throw. Enumeration on unsupported targets throws `UnsupportedOperationException`. This is read-only discovery; the package does not open devices, claim interfaces, or transfer USB data.

[Full typed reference](typed-api.md) · [Getting started](getting-started.md)
