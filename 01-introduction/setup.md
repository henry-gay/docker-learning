# Docker Setup Guide

## Installation Steps
1. **Choose a Supported System**
    - Ensure you have a physical or virtual machine with a supported OS.
    - Example: Ubuntu (64-bit, versions like Bionic, Xenial, etc.).
    - Check your OS version: `cat /etc/os-release`.

2. **Download Docker CE**
    - Visit [docs.docker.com](https://docs.docker.com) and click **Get Docker**.
    - Select your OS (e.g., Linux → Ubuntu) and review prerequisites.

3. **Uninstall Old Versions**
    - Run the command to check and remove any existing Docker versions.

#### Uninstall Docker Desktop on Windows

<details>
  <summary>Steps to Uninstall Docker Desktop</summary>

1. From the Windows Start menu, select **Settings > Apps > Apps & features**.
2. Select **Docker Desktop** from the Apps & features list and then select **Uninstall**.
3. Select **Uninstall** to confirm your selection.

</details>

<details>
  <summary>Uninstall Docker Desktop via CLI</summary>

**Locate the installer:**
  ```
  C:\Program Files\Docker\Docker\Docker Desktop Installer.exe
  ```
**Uninstall Docker Desktop using PowerShell:**
  ```powershell
  Start-Process 'Docker Desktop Installer.exe' -Wait uninstall
  ```
**Uninstall Docker Desktop using Command Prompt:**
  ```cmd
  start /w "" "Docker Desktop Installer.exe" uninstall
  ```

</details>

<details>
  <summary>Remove Residual Files</summary>

    List of Residual Files

    - `C:\ProgramData\Docker`
    - `C:\ProgramData\DockerDesktop`
    - `C:\Program Files\Docker`
    - `C:\Users\<your user name>\AppData\Local\Docker`
    - `C:\Users\<your user name>\AppData\Roaming\Docker`
    - `C:\Users\<your user name>\AppData\Roaming\Docker Desktop`
    - `C:\Users\<your user name>\.docker`
</details>

---

#### Uninstall Docker Desktop on Ubuntu

<details>
  <summary>Steps to Uninstall Docker Desktop</summary>

1. Open a terminal.
2. Run the following command to remove Docker Desktop:
   ```bash
   sudo apt remove docker-desktop
   ```
3. Remove remaining Docker-related dependencies:
   ```bash
   sudo apt purge docker-desktop
   ```
4. Reboot your system to ensure all changes take effect.

</details>

<details>
  <summary>Remove Residual Files</summary>

  <details>
    <summary>List of Residual Files</summary>

    - `~/.docker`
    - `/var/lib/docker`
    - `/var/lib/containerd`
    - `/etc/docker`
    - `/usr/local/bin/docker`
    - `/usr/bin/docker`
    - `/usr/bin/docker-compose`
    - `/usr/share/docker`

  </details>

To remove these files, run:
  ```bash
  sudo rm -rf ~/.docker /var/lib/docker /var/lib/containerd /etc/docker /usr/local/bin/docker /usr/bin/docker /usr/bin/docker-compose /usr/share/docker
  ```

</details>

4. **Install Docker**
    - **Linux Installation**
        - **Option 1: Manual Installation**
            - Update package repository: `sudo apt-get update`
            - Install prerequisites and add Docker’s GPG key.
        - **Option 2: Convenience Script (Recommended)**
            - Download and execute the script:
              ```sh
              curl -fsSL https://get.docker.com -o get-docker.sh
              sudo sh get-docker.sh
              ```
        - Wait for installation to complete.

    - **Windows Installation**
        - Download Docker Desktop from [Docker's official website](https://docs.docker.com/desktop/setup/install/windows-install/).
        - Follow the installation steps and restart your system if needed.
        - Ensure **WSL 2** is enabled for better performance.

    - **Mac Installation**
        - Download Docker Desktop for Mac from [Docker's official website](https://docs.docker.com/desktop/setup/install/mac-install/).
        - Follow installation instructions and verify Docker is running.

5. **Verify Installation**
    - Check Docker version: `docker --version`.
    - Ensure Docker is running properly.

## Running Your First Container
1. **Explore Docker Hub**
    - Visit [hub.docker.com](https://hub.docker.com) to find images like Nginx, MongoDB, Alpine, Node.js, etc.

2. **Run a Test Container**
    - Pull and run the Whalesay image:
      ```sh
      sudo docker run docker/whalesay cowsay "Hello, world!"
      ```
    - Docker will pull the image and display the whale saying "Hello, world!".

## Notes
- You don’t need to set up Docker on your own for this course; hands-on labs are provided.
- However, feel free to install and experiment with Docker locally if you’d like additional practice.