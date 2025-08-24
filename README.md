# Adrenaline Bubble Booter - Archive Repository

[![Status](https://img.shields.io/badge/Status-Archived-lightgrey.svg)](https://github.com/yourusername/Adrenaline-Bubble-Booter)
[![Version](https://img.shields.io/badge/Version-0.5-blue.svg)](https://github.com/yourusername/Adrenaline-Bubble-Booter/releases)
[![License](https://img.shields.io/badge/License-Unlicense-lightgrey.svg)](LICENSE)

> **Note: This is an archive and mirror repository.**
> The original project by LMAN (LeecherMan) has been discontinued and its original homepage is no longer available. This repository exists solely to preserve the source code, compiled binaries, and documentation for historical, educational, and maintenance purposes within the PS Vita homebrew community.

Adrenaline Bubble Booter (C) 2017 LMAN (LeecherMan)

A plugin to directly boot any PSP game (ISO, CSO, PBP, PSOne) from LiveArea bubbles with full feature support.

---

## 📖 Table of Contents

- [Features](#-features)
- [Compatibility](#-compatibility)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Advanced Options](#-advanced-options)
- [Changelog](#-changelog)
- [Troubleshooting](#-troubleshooting)
- [Disclaimer](#-disclaimer)

## ✨ Features

*   **Direct Boot:** Launch PSP ISOs, CSOs, PBPs, and PSOne games directly from any PSP LiveArea bubble.
*   **Full Compatibility:** Works as a separate plugin, maintaining compatibility with updated Adrenaline versions.
*   **Multi-Partition Support:** Boot games from `ux0:`, `ur0:`, or `uma0:` partitions.
*   **Per-Bubble Configuration:**
    *   Choose driver mode: **Inferno** (default), **March33**, or **NP9660**.
    *   Execute **EBOOT.BIN** (default), **EBOOT.OLD**, or **BOOT.BIN** for Prometheus patches.
    *   Enable or disable **all plugins** for each game.
    *   Enable or disable **custom boot images** for each bubble.
*   **Custom Boot Logos:** Use custom 480x272 PNG images as startdat boot logos for each bubble.

## ✅ Compatibility

*   **Requires:** A PS Vita with custom firmware (HENkaku/enso).
*   **Requires:** A fully functional installation of [Adrenaline](https://github.com/TheOfficialFloW/Adrenaline).
*   **Compatible:** Designed to be forward-compatible with new Adrenaline versions.

## 📥 Installation & Configuration

### Prerequisites
1.  Ensure **Adrenaline** is installed and working correctly (`ux0:adrenaline/`).
2.  Your game files (ISO/CSO/PBP) must be placed in the `pspemu` directory (e.g., `ux0:pspemu/ISO/`).

### Steps
1.  **Copy the Plugin:** Extract the `adrbblbooter` folder to the root of your Vita's storage (`ux0:/`).
2.  **Edit Config.txt:** Modify the HENkaku `config.txt` for the PSP bubble's TITLEID (e.g., `NPXX00001`).
    Add the booter plugin line **BEFORE** the adrenaline plugin line.
    ```txt
    *NPXX00001
    ux0:adrbblbooter/adrbblbooter.suprx
    ux0:adrenaline/adrenaline.suprx
    ```
3.  **Reload Config:** Reload the HENkaku configuration via MolecularShell or Settings.
4.  **Create Game Config:** For each bubble you want to configure, create a text file in `ux0:adrbblbooter/bubblesdb/` named after the bubble's TITLEID (e.g., `NPXX00001.txt`).
5.  **Set Game Path:** Inside the text file, add the `ms0:` path to your game file. This path is relative to the `pspemu` folder.
    ```txt
    ms0:/ISO/YourGame.iso
    ```

## ⚙️ Advanced Options

You can append additional options on new lines in the bubble's config file (`NPXX00001.txt`):

```txt
ms0:/ISO/YourGame.iso  # Game Path (Required)
MARCH33                # Driver: INFERNO (Default), MARCH33, NP9660
EBOOT.OLD              # Execute: EBOOT.BIN (Default), EBOOT.OLD, BOOT.BIN
DISABLE                # Plugins: ENABLE (Default, uses CFW settings), DISABLE
DISABLE                # Startdat Image: ENABLE (Default), DISABLE
