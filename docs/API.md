# usbkit

Import `usbkit` (or `usbkit.USBKit`). This focused package owns `USBDiscoverySupported()`, `USBDiscoveryAvailable()` and `USBDevices() As Array Of USBDeviceInfo`. It has no package, container, or external source dependency. Backend modules are implementation details and are non-public imports; their module-scope symbols are globally prefixed to avoid collisions.

Linux sysfs; Windows SetupAPI USB enumerator. macOS is explicitly unsupported. Supported is a compile-target statement, not a runtime verification claim. Availability is a probe, not a promise that enumeration will succeed: Linux opens/closes /sys/bus/usb/devices (no enumeration). Windows tests SetupAPI/kernel32 libraries.

Enumeration is read-only. Empty arrays mean successful enumeration with no results; missing services/libraries, denied access and native errors throw. Missing optional fields are None, present empty strings are Some(""). No absent numeric or powered state is fabricated as zero/False. Snapshot properties are read-only owned copies. Native IDs are observations in their backend namespace, not cross-platform stable identities or openable handles.

Adapter mapping: linuxusb.Devices / WinUSB.PresentDevices → USBDevices; UsbDevice / USBDevice → USBDeviceInfo. Linux sysfs name and Windows PnP instance ID map to Id. Linux IDs/topology become Some; Windows VID/PID parse from the PnP instance ID when present, while bus/device numbers remain None. Linux Product supplies Name; Windows product/serial remain None. Legacy entry modules are unchanged; no forwarding adapter is installed by this change.

Builder registration: name `usbkit`, source `libraries/usbkit`, version `0.1.0`, output `usbkit-0.1.0.buipkg`. All six desktop triples are in the manifest so unsupported-target predicates can be imported; this does not claim an implemented backend on each target. Build with the native package builder described in
[CONTRIBUTING](https://github.com/BuoyBay/usbkit/blob/main/CONTRIBUTING.md).

Supported operations can fail when hardware, services or access are absent; callers must handle those errors. Cross-target compiler checks do not establish native backend behavior.
