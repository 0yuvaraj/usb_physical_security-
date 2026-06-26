# usb_physical_security-
# 🛡️ USB-Port-Sentinel

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)

## Overview
A robust, Windows-based physical security application that manages USB mass storage access via deep registry manipulation. It acts as a strict gatekeeper for your system's physical ports, secured by SMTP-based One-Time Password (OTP) authentication and an OpenCV-powered visual intruder detection system.

## Visuals
*(Replace the placeholder links below with your actual image/gif paths once uploaded to your repository's `assets/` folder)*

**Application Dashboard**
> `![GUI Screenshot](assets/screenshot.png)`
*(Add a brief sentence here describing what the screenshot shows, e.g., "The main Tkinter interface displaying current USBSTOR registry status.")*

**Intruder Detection & OTP Verification**
> `![Webcam Capture GIF](assets/intruder_capture.gif)`
*(Add a brief sentence here, e.g., "The OTP prompt blocking unauthorized access and triggering the OpenCV video capture upon failure.")*

## Key Technical Features
* **System-Level Access Control:** Directly manipulates the Windows Registry (`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\USBSTOR`) to enable or disable Plug and Play for mass storage devices.
* **Privilege Escalation Handling:** Includes automated administrative privilege checking and `ctypes.windll` elevation prompts to ensure registry modifications execute correctly.
* **2FA via SMTP Protocol:** Critical state changes (enabling/disabling ports) are locked behind a dynamic, 8-character OTP sent to pre-configured secure email addresses via `smtplib` and SSL/TLS encryption.
* **Visual Intruder Logging:** Integrates `cv2` (OpenCV) to silently capture a 5-second video feed from the default webcam upon any failed authentication attempt, saving the forensics locally.
* **Activity Auditing:** Maintains an ongoing local text log of all port manipulation attempts, complete with timestamps and execution statuses.

## Installation & Usage

### Prerequisites
* Windows Operating System
* Python 3.8+ installed and added to PATH
* A functional webcam (for intruder detection)
* An App Password generated for your sender email account (Standard passwords will be blocked by Gmail/Outlook SMTP servers).

### Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/YourUsername/USB-Port-Sentinel.git](https://github.com/YourUsername/USB-Port-Sentinel.git)
   cd USB-Port-Sentinel
pip install -r requirements.txt

python src/main.py

⚠️ CRITICAL USAGE NOTE: > This application modifies core system registry files. It must be run with Administrator privileges. If you launch it via a standard user terminal, the script is designed to attempt an automatic restart to request Admin elevation.
