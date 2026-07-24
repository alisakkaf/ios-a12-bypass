# 🔓 iOS A12+ Bypass Toolkit
🔓 Professional iOS Activation Solution for A12+ Devices | iCloud A12+ Bypass | Advanced Unlock Framework | Modern C++20 | Educational &amp; Research Use Only


<div align="center">

[![C++20](https://img.shields.io/badge/C%2B%2B-20-blue.svg)](https://en.cppreference.com/w/cpp/20)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux-lightgrey.svg)]()
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()

**Professional iOS Activation Solution for A12+ Devices**  
*Advanced Unlock Framework Built with Modern C++20 Architecture*

</div>

---

> [!CAUTION]
> **⚠️ EDUCATIONAL USE ONLY ⚠️**
> 
> This software is provided **EXCLUSIVELY FOR EDUCATIONAL AND RESEARCH PURPOSES**.
> 
> - ✅ **Legal Use**: Security research, learning, legitimate device recovery
> - ❌ **Illegal Use**: Unauthorized device access, theft facilitation, malicious activities
> 
> **By using this tool, you accept FULL RESPONSIBILITY for your actions.**  
> Unauthorized access to devices is **ILLEGAL** in most jurisdictions.  
> **Read [DISCLAIMER.md](DISCLAIMER.md) before proceeding.**
> *coming soon gui*
---

## 📖 Overview

The **iOS A12+ Bypass Toolkit** is a state-of-the-art, professional activation solution designed specifically for Apple's **A12 and newer chipsets** (iPhone XS, XR, and later models). Built with modern C++20 principles, this toolkit leverages native **libimobiledevice** integration for direct, low-level communication with iOS devices.

This project represents a complete architectural reimagining of bypass methodologies, featuring:
- 🎯 **Type-Safe Error Handling** using monadic `Result<T>` types
- 🔒 **RAII Resource Management** for automatic cleanup
- 🧵 **Thread-Safe Logging** with source location tracking
- ⚡ **High Performance** with zero-cost abstractions
- 🏗️ **Clean Architecture** with clear separation of concerns

---

## ✨ Key Features

### 🔧 Core Capabilities
- ✅ **Automated GUID Extraction** from device syslogs
- ✅ **Multi-Stage Payload Deployment** via iTunes exploit chain
- ✅ **Device Profile Support** for iPhone & iPad A12+ models
- ✅ **MobileGestalt Cache Overwriting** for persistent activation
- ✅ **Intelligent Retry Mechanism** for robust operation
- ✅ **Dry-Run Mode** for safe testing without modifications

### 💻 Technical Excellence
- 🚀 **Modern C++20 Standard** (concepts, ranges, source_location)
- 📦 **Strong Typing System** preventing common errors at compile-time
- 🎨 **Colored Terminal Output** with ANSI support
- 📊 **Real-Time Progress Tracking** with callback system
- 🔍 **Verbose Debug Logging** for troubleshooting
- 🧪 **Comprehensive Test Suite** with Catch2 framework

---

## 🛠️ Requirements

### Development Environment

| Component | Minimum Version | Recommended |
|-----------|----------------|-------------|
| **Compiler** | Clang 14+ / GCC 11+ | Clang 15+ |
| **CMake** | 3.20+ | 3.25+ |
| **C++ Standard** | C++20 | C++20 |

### System Dependencies

```bash
# macOS (Homebrew)
brew install cmake pkg-config libimobiledevice libplist libzip sqlite3

# The libimobiledevice suite includes:
#   • libimobiledevice-1.0
#   • libusbmuxd-2.0
#   • libplist-2.0
#   • libimobiledevice-glue-1.0
```

---

## 🚀 Building from Source

### Standard Build

```bash
git clone https://github.com/alisakkaf/ios-a12-bypass.git
cd ios-a12-bypass
mkdir build && cd build
cmake ..
make -j$(nproc)
```

###  Build Options

```bash
# Debug build with full symbols
cmake -DCMAKE_BUILD_TYPE=Debug ..

# Optimized release build
cmake -DCMAKE_BUILD_TYPE=Release ..

# Build without tests
cmake -DBUILD_TESTS=OFF ..
```

### 🧪 Running Tests

```bash
cd build
ctest --output-on-failure
```

---

## 📱 Usage Guide

### Basic Operation

```bash
# Interactive mode (prompts for input)
./a12_bypass

# Fully automated mode
./a12_bypass --auto

# Use pre-extracted GUID
./a12_bypass --guid 2A22A82B-C342-444D-972F-5270FB5080DF
```

### Command-Line Options

#### 🎯 **Operation Modes**
| Flag | Description |
|------|-------------|
| `-a, --auto` | Automated execution (skip prompts, auto-detect GUID) |
| `-n, --dry-run` | Simulation mode (preview without changes) |
| `-l, --list` | Display all compatible device models |
| `-i, --info` | Show detailed connected device information |

#### ⚙️ **Configuration**
| Flag | Description |
|------|-------------|
| `-g, --guid GUID` | Provide pre-extracted SystemGroup GUID |
| `-o, --output DIR` | Specify payload generation directory |
| `-t, --timeout SECS` | Device reconnection timeout (default: 300s) |
| `-r, --retries N` | Maximum GUID extraction attempts (default: 5) |

#### 📊 **Output Control**
| Flag | Description |
|------|-------------|
| `-v, --verbose` | Enable detailed diagnostic logging |
| `-q, --quiet` | Suppress non-essential output |
| `--no-color` | Disable ANSI color formatting |
| `--no-banner` | Skip startup banner display |

#### ℹ️ **Information**
| Flag | Description |
|------|-------------|
| `-h, --help` | Display comprehensive help guide |
| `--version` | Show version and build information |

---

## 📋 Supported Devices

### iPhones (A12 - A17 Pro)

| Model | Marketing Name | Chip |
|-------|----------------|------|
| iPhone11,2 | iPhone XS | A12 Bionic |
| iPhone11,4/6 | iPhone XS Max | A12 Bionic |
| iPhone11,8 | iPhone XR | A12 Bionic |
| iPhone12,1 | iPhone 11 | A13 Bionic |
| iPhone12,3 | iPhone 11 Pro | A13 Bionic |
| iPhone12,5 | iPhone 11 Pro Max | A13 Bionic |
| iPhone13,1 | iPhone 12 mini | A14 Bionic |
| iPhone13,2 | iPhone 12 | A14 Bionic |
| iPhone13,3 | iPhone 12 Pro | A14 Bionic |
| iPhone13,4 | iPhone 12 Pro Max | A14 Bionic |
| iPhone14,2 | iPhone 13 | A15 Bionic |
| iPhone14,5 | iPhone 13 Pro | A15 Bionic |
| iPhone14,3 | iPhone 13 Pro Max | A15 Bionic |
| iPhone15,2 | iPhone 14 Pro | A16 Bionic |
| iPhone15,3 | iPhone 14 Pro Max | A16 Bionic |
| iPhone16,1 | iPhone 15 Pro | A17 Pro |
| iPhone16,2 | iPhone 15 Pro Max | A17 Pro |

### iPads (A12 - M1)

| Model | Marketing Name | Chip |
|-------|----------------|------|
| iPad8,1-4 | iPad Pro 11" (3rd gen) | A12X Bionic |
| iPad8,5-8 | iPad Pro 12.9" (3rd gen) | A12X Bionic |
| iPad11,1-2 | iPad mini (5th gen) | A12 Bionic |
| iPad13,1-2 | iPad Air (4th gen) | A14 Bionic |

> **Note**: Run `./a12_bypass --list` to see all supported models with your current resources.

---

## 🏗️ Project Architecture

```
ios-a12-bypass/
├── 📁 include/iCloudBypassA12/       # Public headers
│   ├── core/                   # Core types & utilities
│   │   ├── types.hpp          # Strong types, constants
│   │   ├── result.hpp         # Monadic error handling
│   │   ├── error.hpp          # Error codes & Error class
│   │   ├── logger.hpp         # Thread-safe logger
│   │   └── raii.hpp           # RAII wrappers
│   ├── device/                 # Device communication
│   │   ├── device_manager.hpp # Device detection/connection
│   │   ├── afc_client.hpp     # Apple File Conduit
│   │   ├── diagnostics_client.hpp  # Device control
│   │   └── syslog_client.hpp  # Syslog relay
│   ├── payload/                # Payload generation
│   │   ├── sqlite_builder.hpp # SQLite database builder
│   │   ├── epub_builder.hpp   # EPUB/ZIP creator
│   │   └── payload_generator.hpp  # Orchestrator
│   ├── utils/                  # Utilities
│   │   ├── guid_extractor.hpp # GUID extraction logic
│   │   └── plist_utils.hpp    # Property list helpers
│   └── bypass/                 # Main bypass logic
│       ├── config.hpp         # Configuration & constants
│       └── bypass_controller.hpp  # Orchestrator
├── 📁 src/                     # Implementation files
│   ├── main.cpp               # CLI entry point
│   ├── core/                  # Core implementations
│   ├── device/                # Device implementations
│   ├── payload/               # Payload implementations
│   ├── utils/                 # Utility implementations
│   └── bypass/                # Bypass implementations
├── 📁 tests/                   # Unit tests (Catch2)
├── 📁 resources/               # Device-specific resources
│   └── plists/                # MobileGestalt plist files
├── CMakeLists.txt             # Build configuration
└── README.md                  # This file
```

---

## 🔬 How It Works

The bypass procedure follows a sophisticated multi-stage exploitation chain:

### Stage 1: Device Detection
1. Connect to device via USB using `libimobiledevice`
2. Query device information (model, iOS version, UDID, etc.)
3. Verify device compatibility with A12+ chipset requirements

### Stage 2: GUID Extraction
1. Trigger device reboot via diagnostics service
2. Establish syslog relay connection
3. Monitor system logs for `BLDatabaseManager.sqlite` path (bookassetd)
4. Extract **SystemGroup GUID** from the filesystem path

### Stage 3: Payload Generation
1. Load device-specific `MobileGestalt.plist` from resources
2. Generate `downloads.28.sqlitedb` with trigger record
3. Create `BLDatabaseManager.sqlite` with path traversal exploit
4. Build `asset.epub` (fixedfile) containing MobileGestalt plist
5. Craft `iTunesMetadata.plist` with SystemGroup path reference

### Stage 4: Payload Deployment
1. Establish AFC (Apple File Conduit) connection
2. Clean old bypass artifacts if present
3. Upload generated payloads to `/iTunes_Control/iTunes/`
4. Verify successful upload

### Stage 5: Multi-Stage Exploitation
**Stage 1 - itunesstored Trigger:**
- Reboot device to trigger `itunesstored` daemon
- itunesstored processes `downloads.28.sqlitedb`
- Daemon extracts `iTunesMetadata.plist`

**Stage 2 - bookassetd Trigger:**
- Copy metadata to `/Books/` directory
- Reboot to trigger `bookassetd` daemon
- bookassetd downloads and extracts `asset.epub`
- Path traversal writes MobileGestalt to SystemGroup container

**Stage 3 - Final Persistence:**
- Final reboot loads new MobileGestalt cache
- Device activation state is bypassed

---

## ⚠️ Troubleshooting

### Common Issues

#### ❌ "Device not found"
**Solutions:**
- Verify USB cable connection
- Trust computer on device (check for trust prompt)
- Run `idevice_id -l` to verify libimobiledevice can see device
- Try different USB port or cable

#### ❌ "Failed to start lockdown service"
**Solutions:**
- Device needs to be re-trusted
- Disconnect and reconnect USB
- Reboot both device and computer

#### ❌ "GUID extraction failed"
**Solutions:**
- Ensure device can complete full boot cycle
- Increase syslog timeout: `--timeout 400`
- Increase retry attempts: `--retries 10`
- Use manual GUID input mode (without `--auto`)

#### ❌ Build errors about missing headers
**Solutions:**
```bash
# Verify pkg-config can find libraries
pkg-config --cflags libimobiledevice-1.0
pkg-config --libs libimobiledevice-1.0

# Reinstall dependencies
brew reinstall libimobiledevice libplist libzip
```

---

## 📄 License

This project is licensed under the **MIT License** - see below for details:

```
MIT License

Copyright (c) 2025 iOS A12+ Bypass Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## ⚖️ Legal Disclaimer

> **IMPORTANT**: This tool is provided **for educational and research purposes only**.
>
> - ✅ **Intended Use**: Legitimate device recovery and security research
> - ❌ **Prohibited Use**: Unauthorized access to devices you do not own
> - ⚠️ **Your Responsibility**: Ensure compliance with local laws and regulations
>
> The developers assume **NO LIABILITY** for misuse of this software. By using this tool, you acknowledge that you are solely responsible for your actions and their consequences.

---

## 🙏 Acknowledgments

### Technology Stack
- **libimobiledevice** - The backbone of iOS device communication
- **libplist** - Property list parsing and manipulation
- **libzip** - ZIP/EPUB archive creation
- **SQLite3** - Database generation utilities
- **Catch2** - Modern C++ testing framework

### Community
- Original Python implementation researchers
- Modern C++20 patterns and best practices community
- Open-source iOS security research contributors


---

### 💡 Support the Developer

<div align="center">
  <i>If you find my tools and projects useful, consider supporting my work. Your support helps keep these projects completely free!</i>
</div>

<br>

<div align="center">

| Crypto Asset | Network | Wallet Address (Copy) | Quick Scan |
| :--- | :--- | :--- | :---: |
| ![USDT](https://img.shields.io/badge/USDT-Tether-26A17B?style=for-the-badge&logo=tether&logoColor=white) | **TRC20** | `TYLBeDA5aGNcc3WkVqf3xWPHXmsZzs2p28` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=TYLBeDA5aGNcc3WkVqf3xWPHXmsZzs2p28" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |
| ![USDT](https://img.shields.io/badge/USDT-Tether-26A17B?style=for-the-badge&logo=tether&logoColor=white) | **BEP20** | `0x67cf27f33c80479ea96372810f9e2ee4c3b095c5` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=0x67cf27f33c80479ea96372810f9e2ee4c3b095c5" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |
| ![BTC](https://img.shields.io/badge/BTC-Bitcoin-F7931A?style=for-the-badge&logo=bitcoin&logoColor=white) | **Bitcoin** | `bc1q97dr37h37npzarmmrv0tjz2nm50htqc7pfpzj6` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=bitcoin:bc1q97dr37h37npzarmmrv0tjz2nm50htqc7pfpzj6" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |
| ![ETH](https://img.shields.io/badge/ETH-Ethereum-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white) | **ERC20** | `0x67cf27f33c80479ea96372810F9e2EE4C3b095C5` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=ethereum:0x67cf27f33c80479ea96372810F9e2EE4C3b095C5" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |
| ![SOL](https://img.shields.io/badge/SOL-Solana-9945FF?style=for-the-badge&logo=solana&logoColor=white) | **Solana** | `Cbesgr4tvo4T1inNMFe46GSym2qMYjkmofbXFc77rDNK` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=solana:Cbesgr4tvo4T1inNMFe46GSym2qMYjkmofbXFc77rDNK" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |
| ![USDC](https://img.shields.io/badge/USDC-USD_Coin-2775CA?style=for-the-badge&logo=usd-coin&logoColor=white) | **ERC20** | `0x67cf27f33c80479ea96372810f9e2ee4c3b095c5` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=0x67cf27f33c80479ea96372810f9e2ee4c3b095c5" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |
| ![USDC](https://img.shields.io/badge/USDC-USD_Coin-2775CA?style=for-the-badge&logo=usd-coin&logoColor=white) | **SPL** | `Cbesgr4tvo4T1inNMFe46GSym2qMYjkmofbXFc77rDNK` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=solana:Cbesgr4tvo4T1inNMFe46GSym2qMYjkmofbXFc77rDNK" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |
| ![USDC](https://img.shields.io/badge/USDC-USD_Coin-2775CA?style=for-the-badge&logo=usd-coin&logoColor=white) | **BEP20** | `0x67cf27f33c80479ea96372810F9e2EE4C3b095C5` | <a href="https://api.qrserver.com/v1/create-qr-code/?size=300x300&margin=10&data=0x67cf27f33c80479ea96372810F9e2EE4C3b095C5" target="_blank"><img src="https://img.shields.io/badge/Show_QR-Click_Here-black?style=flat-square&logo=qr-code" alt="QR"></a> |

</div>

---

## 📞 Support & Contact

- **GitHub**: [@alisakkaf](https://github.com/alisakkaf)
- **Facebook**: [Ali Sakkaf - Developer](https://www.facebook.com/AliSakkaf.Dev/)
- **Issues**: [Report bugs or request features](https://github.com/alisakkaf/ios-a12-bypass/issues)

---

<div align="center">

**Made with ❤️ using Modern C++20**

*Star ⭐ this repository if you find it useful!*

</div>
