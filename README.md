![Pigeon](https://raw.githubusercontent.com/ArnabBir/pigeon-releases/main/assets/icon.png)

# Pigeon

### The Universal Client for Every Network Protocol

[![Latest Release](https://img.shields.io/github/v/release/ArnabBir/pigeon-releases?style=flat-square&color=5DA9E9&label=Latest)](https://github.com/ArnabBir/pigeon-releases/releases)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=flat-square)](https://github.com/ArnabBir/pigeon-releases/blob/main/LICENSE)
[![Platforms](https://img.shields.io/badge/Platforms-macOS%20·%20Windows%20·%20Linux-lightgrey?style=flat-square)](https://github.com/ArnabBir/pigeon-releases/releases)

[**Download**](https://github.com/ArnabBir/pigeon-releases/releases) · [**All Releases**](https://github.com/ArnabBir/pigeon-releases/releases) · [**Report an Issue**](https://github.com/ArnabBir/pigeon-releases/issues)

---

> *Pigeon is a desktop application designed for developers who work across protocols. It brings HTTP, GraphQL, WebSocket, Server Sent Events, TCP, UDP, MQTT, and Socket.IO into a single, refined interface. No browser extensions required. No accounts. No telemetry. Just a clean workspace that stays out of your way.*

---

## Demo

[![Watch Pigeon in Action](https://img.youtube.com/vi/b7LVhT8OmOA/maxresdefault.jpg)](https://www.youtube.com/watch?v=b7LVhT8OmOA)

[**Watch the full demo on YouTube**](https://www.youtube.com/watch?v=b7LVhT8OmOA)

---

## Protocols

| Protocol | Description |
|:--|:--|
| **HTTP / REST** | Full method support with headers, authentication, body types, and response inspection |
| **GraphQL** | Dedicated query editor with variables, introspection, and an interactive explorer |
| **WebSocket** | Bidirectional messaging with connection lifecycle management and message filtering |
| **Server Sent Events** | One way streaming with event type filtering and auto reconnect |
| **TCP** | Raw socket communication through a lightweight local relay |
| **UDP** | Datagram messaging with built in DNS lookup demonstrations |
| **MQTT** | Publish and subscribe to IoT topics with full client controls |
| **Socket.IO** | Namespace and room aware client with authentication support |

## Downloads

All builds are available on the [**Releases**](https://github.com/ArnabBir/pigeon-releases/releases) page.

### macOS

| Architecture | Format | Link |
|:--|:--|:--|
| Apple Silicon (M1, M2, M3, M4) | DMG | [Download from Releases](https://github.com/ArnabBir/pigeon-releases/releases) |
| Intel (x64) | DMG | [Download from Releases](https://github.com/ArnabBir/pigeon-releases/releases) |

**Homebrew** (recommended):

```
brew tap ArnabBir/pigeon https://github.com/ArnabBir/homebrew-pigeon.git
brew install --cask pigeon
```

### Windows

| Architecture | Format | Link |
|:--|:--|:--|
| x64 | Setup Installer (.exe) | [Download from Releases](https://github.com/ArnabBir/pigeon-releases/releases) |

### Linux

| Format | Link |
|:--|:--|
| AppImage | [Download from Releases](https://github.com/ArnabBir/pigeon-releases/releases) |
| DEB (Debian, Ubuntu) | [Download from Releases](https://github.com/ArnabBir/pigeon-releases/releases) |

## Installation

### macOS

**Via Homebrew:**

```
brew tap ArnabBir/pigeon https://github.com/ArnabBir/homebrew-pigeon.git
brew install --cask pigeon
```

**Manual installation:**

Download the DMG for your architecture from [Releases](https://github.com/ArnabBir/pigeon-releases/releases). Open the disk image and drag Pigeon into Applications.

If macOS reports the application as unverified:

```
sudo xattr -cr /Applications/Pigeon.app
```

### Windows

Download the installer from [Releases](https://github.com/ArnabBir/pigeon-releases/releases). Right click the `.exe` file and select *Run as Administrator*. Follow the setup wizard. Pigeon will appear in the Start Menu once complete.

> Windows Defender may flag unsigned applications. Select *More info* followed by *Run anyway* to proceed.

### Linux

**AppImage:**

```
chmod +x Pigeon-*.AppImage
./Pigeon-*.AppImage
```

**DEB package:**

```
sudo apt install ./Pigeon-*.deb
```

## Capabilities

### Request Authoring

Full featured request editor supporting all standard HTTP methods. Configurable headers with autocomplete. Multiple body formats including JSON, form data, URL encoded, and raw text. Authentication via Bearer tokens, Basic Auth, and API keys. Environment variables for dynamic values across requests.

### Collections and Runner

Organize requests into named collections with folder hierarchies. Execute collections sequentially with the built in runner. Define assertions on status codes, response bodies, headers, and timing. Export results as JSON for CI pipelines or as HTML for human review.

### Response Analysis

Automatic content type detection for JSON, HTML, and XML. Collapsible tree views for structured data. Response metadata including status, latency, and payload size. Click to copy for any value, path, or header.

### Real Time Protocols

WebSocket connections with full send and receive history. SSE streams with event type filtering. TCP and UDP via a lightweight local relay that bridges the browser sandbox.

### Developer Tools

Import from Swagger, OpenAPI, Postman, and cURL. Code generation for multiple languages. Request benchmarking with latency distribution analysis. Mock server for local development. Network capture and cookie management. Contract testing and API monitoring.

### Privacy

All data remains on your machine. There are no accounts, no cloud sync, and no usage telemetry. Storage is entirely local.

## System Requirements

| Platform | Minimum Version |
|:--|:--|
| macOS | 10.15 Catalina or later (Intel and Apple Silicon) |
| Windows | 10 or later |
| Linux | glibc 2.29+ with libfuse2 |

## Verifying Downloads

Every release includes SHA 256 checksums. After downloading, verify the integrity of your files:

```
sha256sum -c SHA256SUMS
```

## Troubleshooting

**macOS blocks the application as unidentified**

```
sudo xattr -cr /Applications/Pigeon.app
```

**Homebrew upgrade encounters a Swift compiler error**

Reinstall Xcode Command Line Tools:

```
xcode-select --install
```

If the issue persists:

```
sudo rm -rf /Library/Developer/CommandLineTools
xcode-select --install
```

**Windows Defender blocks the installer**

Select *More info* on the SmartScreen prompt, then choose *Run anyway*.

**AppImage does not launch on Linux**

Ensure the file has execute permissions and the required dependency is present:

```
chmod +x Pigeon-*.AppImage
sudo apt install libfuse2
```

**DEB installation reports missing dependencies**

```
sudo apt install -f ./Pigeon-*.deb
```

## Technology

Built with Electron, React, TypeScript, and Tailwind CSS. State management by Zustand. Syntax highlighting by Prism.

## Author

**Arnab Bir**

[arnabbir.github.io](https://arnabbir.github.io) · [arnabbir@gmail.com](mailto:arnabbir@gmail.com) · [LinkedIn](https://www.linkedin.com/in/arnabbir) · [Substack](https://substack.com/@arnabbir) · [X](https://x.com/arnabbir)

## License

Licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).

You may use, distribute, and modify this software under the terms of the Apache 2.0 license. A copy of the license is included in this repository.

```
Copyright 2025 Arnab Bir

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

---

*Pigeon is built for developers, by a developer.*
