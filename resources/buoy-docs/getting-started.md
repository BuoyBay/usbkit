---
title: "Getting started with usbkit"
summary: "Import usbkit, check platform availability, and handle results and failures."
category: "Guide"
order: 10
keywords: ["usbkit", "USBKit", "native", "discovery"]
symbols: ["USBDeviceInfo", "USBDevices", "USBDiscoverySupported", "USBDiscoveryAvailable"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

Install `usbkit` into your project’s packages directory with your package workflow, then import `usbkit`. Use the USBKit facade instead of importing platform backend modules.

Check `USBDiscoverySupported()`, then probe `USBDiscoveryAvailable()`. Call `USBDevices()` inside your application’s exception handling and display its `Array Of USBDeviceInfo`. Keep optional fields optional when formatting the result, and request a fresh snapshot when the user refreshes.

## Handling availability

A Supported predicate describes the compile target. An Available predicate probes runtime prerequisites; it does not guarantee that the next operation will succeed. Preserve the distinction between successful empty results and an exception. Consult the [API contracts](api.md) for supported platforms, blocking behavior, and lifecycle requirements.

The [typed reference](typed-api.md) lists argument types, defaults, read-only properties, and return values. It also includes declarations from internal backend source modules; applications should use the facade entry points described here.
