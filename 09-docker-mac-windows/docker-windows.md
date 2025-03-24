# Docker on Windows

## Understanding Docker and OS Compatibility
Containers share the underlying OS kernel, meaning **Windows containers cannot run on Linux hosts** and vice versa. This is a fundamental concept in Docker that is important to remember.

## Docker on Windows: Available Options
There are two ways to run Docker on Windows:

### 1. Docker Toolbox (Legacy Solution)
Docker Toolbox was the original way to run Docker on Windows, primarily for older versions of Windows.

#### How It Works:
- Requires **Oracle VirtualBox** or **VMware Workstation**.
- Deploys a lightweight Linux VM (Boot2Docker) on Windows.
- Docker runs inside the Linux VM, not natively on Windows.

#### Requirements:
- **Windows 7 (64-bit) or higher**.
- Virtualization must be enabled in BIOS.
- Contains **Docker Engine, Docker Machine, Docker Compose, and Kitematic**.

> ⚠ **Docker Toolbox is a legacy solution** for older Windows systems that don’t support newer Docker options.

### 2. Docker Desktop for Windows (Modern Solution)
Docker Desktop for Windows is the current, preferred method for running Docker natively on Windows.

#### How It Works:
- Uses **Microsoft Hyper-V** instead of VirtualBox.
- Creates a Linux VM inside Hyper-V and runs Docker inside it.
- Supported on **Windows 10 Pro, Enterprise, and Windows Server 2016** (Hyper-V required).

#### Key Differences:
- **Docker Toolbox uses VirtualBox**, while **Docker Desktop uses Hyper-V**.
- **More efficient, native Windows integration with Docker Desktop**.

## Running Linux vs. Windows Containers
Docker Desktop for Windows supports **both Linux and Windows containers**.

- **Default Mode:** Runs Linux containers.
- **Switching to Windows Containers:**
  ```sh
  docker run --isolation=hyperv my-windows-app
  ```
  or switch through the Docker Desktop settings.

### Windows Containers vs. Linux Containers
| Feature | Linux Containers | Windows Containers |
|---------|----------------|-----------------|
| Kernel Sharing | Yes | Yes (Windows Server Containers) |
| Isolation | Process-based | Hyper-V Isolation |
| Base Images | Ubuntu, Debian, Alpine | Windows Server Core, Nano Server |

## Types of Windows Containers
1. **Windows Server Containers:**
    - Shares OS kernel with the host.
    - Similar to Linux containers.

2. **Hyper-V Isolation:**
    - Each container runs inside an optimized VM.
    - Provides full kernel isolation for security.

## Windows Base Images
- **Windows Server Core:** Standard Windows image, not as lightweight.
- **Nano Server:** Minimal, headless Windows OS (like Alpine for Linux).

## Important Notes on Windows and Docker
- Windows containers are supported on **Windows Server 2016, Nano Server, and Windows 10 Pro/Enterprise**.
- **Windows 10 only supports Hyper-V isolated containers.**
- **VirtualBox and Hyper-V cannot coexist.** If using Docker Toolbox (VirtualBox) and switching to Docker Desktop (Hyper-V), migration is required.

For more information, refer to Docker’s official migration guide from VirtualBox to Hyper-V.

---
Now that you understand Docker on Windows, try setting up Docker Desktop and running both Linux and Windows containers!