---
title: "usbkit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["USBDeviceInfo", "USBKitLinuxUsbDevice", "USBKitWindowsNativeUSBDeviceInfo", "USBKitWindowsUSBDevice"]
dependencies: []
symbols: ["USBDeviceInfo", "USBKitLinuxUsbDevice", "USBKitWindowsNativeUSBDeviceInfo", "USBKitWindowsUSBDevice"]
related: ["api.md", "getting-started.md", "index.md"]
---

# usbkit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## USBDeviceInfo

`Public Class USBDeviceInfo`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Id` | `String` | Yes | No | — | — |
| `VendorId` | `Optional Of Integer` | Yes | No | — | — |
| `ProductId` | `Optional Of Integer` | Yes | No | — | — |
| `BusNumber` | `Optional Of Integer` | Yes | No | — | — |
| `DeviceNumber` | `Optional Of Integer` | Yes | No | — | — |
| `Name` | `Optional Of String` | Yes | No | — | — |
| `Manufacturer` | `Optional Of String` | Yes | No | — | — |
| `Product` | `Optional Of String` | Yes | No | — | — |
| `SerialNumber` | `Optional Of String` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(vId As String, vVendorId As Optional Of Integer, vProductId As Optional Of Integer, vBusNumber As Optional Of Integer, vDeviceNumber As Optional Of Integer, vName As Optional Of String, vManufacturer As Optional Of String, vProduct As Optional Of String, vSerialNumber As Optional Of String)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `vId` | `String` | `ByVal` | Required |
| `vVendorId` | `Optional Of Integer` | `ByVal` | Required |
| `vProductId` | `Optional Of Integer` | `ByVal` | Required |
| `vBusNumber` | `Optional Of Integer` | `ByVal` | Required |
| `vDeviceNumber` | `Optional Of Integer` | `ByVal` | Required |
| `vName` | `Optional Of String` | `ByVal` | Required |
| `vManufacturer` | `Optional Of String` | `ByVal` | Required |
| `vProduct` | `Optional Of String` | `ByVal` | Required |
| `vSerialNumber` | `Optional Of String` | `ByVal` | Required |

Returns: no value.

## USBKit functions

### USBDiscoverySupported

`Public Function USBDiscoverySupported() As Boolean`

Read-only compile-target backend test; no runtime I/O.

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### USBDiscoveryAvailable

`Public Function USBDiscoveryAvailable() As Boolean`

Read-only: Linux opens/closes the USB sysfs directory; Windows probes libraries only.

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### USBDevices

`Public Function USBDevices() As Array Of USBDeviceInfo`

Read-only snapshot; errors throw, successful absence returns an empty array. IDs are native observations.

No parameters.

#### Returns

| Type |
| --- |
| `Array Of USBDeviceInfo` |

## USBKitLinuxUsbDevice

`Public Class USBKitLinuxUsbDevice`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `SysfsName` | `String` | No | No | — | — |
| `SysfsPath` | `String` | No | No | — | — |
| `VendorId` | `Integer` | No | No | — | — |
| `ProductId` | `Integer` | No | No | — | — |
| `BusNumber` | `Integer` | No | No | — | — |
| `DeviceNumber` | `Integer` | No | No | — | — |
| `DevicePath` | `Optional Of String` | No | No | — | — |
| `Manufacturer` | `Optional Of String` | No | No | — | — |
| `Product` | `Optional Of String` | No | No | — | — |
| `SerialNumber` | `Optional Of String` | No | No | — | — |

## USBKitLinuxBackend functions

### USBKitLinuxIsSupported

`Public Function USBKitLinuxIsSupported() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### USBKitLinuxDevices

`Public Function USBKitLinuxDevices(sysfsRoot As String = "/sys/bus/usb/devices") As Array Of USBKitLinuxUsbDevice`

Enumerate a sysfs USB bus tree, including root hubs; missing/unreadable trees throw.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `sysfsRoot` | `String` | `ByVal` | `"/sys/bus/usb/devices"` |

#### Returns

| Type |
| --- |
| `Array Of USBKitLinuxUsbDevice` |

### USBKitLinuxProbe

`Public Function USBKitLinuxProbe() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

## USBKitWindowsUSBDevice

`Public Class USBKitWindowsUSBDevice`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `InstanceId` | `String` | No | No | — | — |
| `Name` | `Optional Of String` | No | No | — | — |
| `Manufacturer` | `Optional Of String` | No | No | — | — |
| `DeviceNode` | `Integer` | No | No | — | — |

## USBKitWindowsNativeUSBDeviceInfo

`Sequential Structure USBKitWindowsNativeUSBDeviceInfo`

### Fields

| Name | Type | Value / Default | Description |
| --- | --- | --- | --- |
| `Size` | `UInt32` | — | — |
| `GuidA` | `UInt32` | — | — |
| `GuidB` | `UInt32` | — | — |
| `GuidC` | `UInt32` | — | — |
| `GuidD` | `UInt32` | — | — |
| `DeviceNode` | `UInt32` | — | — |
| `Reserved` | `UInt64` | — | — |

## USBKitWindowsBackend functions

### USBKitWindowsIsSupported

`Public Function USBKitWindowsIsSupported() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### USBKitWindowsIsAvailable

`Public Function USBKitWindowsIsAvailable() As Boolean`

Library availability only; an installed backend can have no present hardware.

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### USBKitWindowsPresentDevices

`Public Function USBKitWindowsPresentDevices() As Array Of USBKitWindowsUSBDevice`

One owned record per present USB device node; discovery can race hotplug.

No parameters.

#### Returns

| Type |
| --- |
| `Array Of USBKitWindowsUSBDevice` |
