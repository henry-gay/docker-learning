# Docker on Mac

## Overview
Docker on Mac is similar to Docker on Windows, providing two ways to run Linux containers on macOS:
1. **Docker Toolbox** (Legacy Solution)
2. **Docker Desktop for Mac** (Modern Solution)

---

## 1. Docker Toolbox (Legacy Solution)
Docker Toolbox was the original way to run Docker on Mac, utilizing **VirtualBox** to create a Linux VM.

### How It Works:
- Installs **Oracle VirtualBox**, **Docker Engine**, **Docker Machine**, **Docker Compose**, and **Kitematic**.
- Deploys a lightweight VM called **Boot2Docker** that runs Docker.
- Supports **macOS 10.8 or newer**.

> ⚠ **Docker Toolbox is a legacy solution** and has been replaced by Docker Desktop for Mac.

---

## 2. Docker Desktop for Mac (Modern Solution)
Docker Desktop for Mac is the preferred method for running Docker on macOS.

### How It Works:
- Uses **HyperKit**, a lightweight macOS-native hypervisor, instead of VirtualBox.
- Automatically creates a Linux system under the hood to run Docker.
- Supports **macOS Sierra 10.12 or newer**.
- Requires a **Mac from 2010 or newer**.

### Key Differences:
| Feature           | Docker Toolbox | Docker Desktop for Mac |
|------------------|---------------|----------------------|
| Virtualization   | VirtualBox    | HyperKit            |
| Performance      | Lower         | Higher              |
| macOS Version   | 10.8+         | 10.12+              |

---

## Running Linux Containers on Mac
- Both **Docker Toolbox** and **Docker Desktop for Mac** are designed to run **Linux containers**.
- **There are no native Mac-based images or containers**.

---

## Summary
- **Docker Toolbox** (uses VirtualBox) is outdated.
- **Docker Desktop for Mac** (uses HyperKit) is the preferred solution.
- Docker on Mac only runs **Linux containers**, not macOS-based containers.

Now, set up Docker Desktop for Mac and start working with containers!