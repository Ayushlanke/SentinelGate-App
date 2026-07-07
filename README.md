# SentinelGate — Companion Mobile Application

[![Flutter](https://img.shields.io/badge/Platform-Flutter-blue.svg)](https://flutter.dev/)
[![Android](https://img.shields.io/badge/Platform-Android-green.svg)](https://developer.android.com/)
[![Release](https://img.shields.io/badge/Release-APK%20Ready-success.svg)](release/Siddhivinayak Access.apk)

Official companion mobile application for the **SentinelGate** smart lock system deployed at **Siddhivinayak CHS (Co-operative Housing Society)**.

This application allows authorized residents to unlock the society gate using secure **Bluetooth Low Energy (BLE)** communication or **Phone NFC Card Emulation**, providing a completely offline, cloud-independent access control experience.

> **Firmware Repository:**  
> https://github.com/Ayushlanke/SentinelGate

---

# 🏢 About the Project

This application was specifically developed for **Siddhivinayak CHS** as the mobile companion to the **SentinelGate** smart lock system.

Together, the firmware and mobile application provide:

- Offline-first authentication
- Secure BLE communication
- Phone NFC tap-to-unlock
- No cloud dependency
- Fast resident registration
- Enterprise-grade cryptographic authentication

The firmware running on the gate controller is available here:

**SentinelGate Firmware Repository**

https://github.com/Ayushlanke/SentinelGate

---

# 📱 Features

## 🔓 BLE Unlock

Residents can securely unlock the main gate using Bluetooth Low Energy.

- Encrypted communication
- Authenticated unlock requests
- Typical operating range up to **5 meters**
- Works entirely offline

---

## 📲 Phone NFC Tap-to-Unlock

Supported Android devices can emulate an NFC access card.

Simply:

1. Enable NFC
2. Hold the phone against the SentinelGate reader
3. The gate unlocks instantly

The application supports NFC card emulation, allowing access even when the application is running in the background.

---

## 🏠 Resident Registration

Each resident registers only once using:

- Room Number
- 6-Digit Join Code

Registration is verified locally through Bluetooth communication with the SentinelGate controller.

After successful registration, encrypted credentials are securely stored on the device.

---

## 🌐 Completely Offline

No internet connection is required.

The system operates without:

- Cloud servers
- Wi-Fi
- Mobile data
- External authentication services

This ensures uninterrupted access during internet outages and provides improved privacy.

---

# 🔒 Android Permissions

The application requires the following permissions for local hardware communication.

| Permission | Purpose |
|------------|---------|
| Bluetooth / Bluetooth Connect / Bluetooth Scan | Discover and communicate with the SentinelGate controller |
| Fine & Coarse Location | Required by Android for BLE scanning only. The application does **not** collect or transmit location data. |
| NFC | Enables communication with the SentinelGate NFC reader using phone card emulation. |

---

# 🔐 Security Architecture

Every unlock request is cryptographically authenticated.

## HMAC-SHA256 Authentication

Each request is signed using:

```
Signature = HMAC-SHA256(
    SharedSecret,
    RoomNumber + Timestamp
)
```

The shared secret is generated on the SentinelGate controller and never transmitted over the air.

---

## Replay Attack Protection

Every authentication packet includes a timestamp.

Requests automatically expire after **30 seconds**, preventing replay attacks.

---

## Automatic Time Synchronization

During authentication, the mobile application provides its current timestamp.

The SentinelGate controller uses this information to:

- Maintain accurate event logs
- Keep replay protection synchronized
- Reduce clock drift

---

# 📦 Repository Contents

```
release/
└── Siddhivinayak Access.apk
```

This repository distributes the production Android APK used by residents of **Siddhivinayak CHS**.

The Flutter source code remains private to protect:

- Security architecture
- Authentication protocols
- Cryptographic implementation
- NFC communication logic
- BLE protocol details

---

# 📥 Installation

1. Download **release/Siddhivinayak Access.apk**
2. Install the APK on an Android device.
3. If prompted, enable **Install from Unknown Sources**.
4. Open the application.
5. Enable:
   - Bluetooth
   - NFC
   - Required permissions
6. Register using the Room Number and Join Code provided by the society administrator.

---

# 🔗 Related Project

This application is the official mobile companion for the **SentinelGate** smart lock firmware developed for **Siddhivinayak CHS**.

Firmware Repository:

**SentinelGate**

https://github.com/Ayushlanke/SentinelGate

---

## © Project

Developed for **Siddhivinayak CHS** as part of the **SentinelGate Offline Smart Lock System**.

SentinelGate combines secure BLE communication, NFC access, and offline cryptographic authentication to provide a modern, reliable, and cloud-independent residential access control solution.