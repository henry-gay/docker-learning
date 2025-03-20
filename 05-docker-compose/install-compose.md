# Installing Docker Compose

Docker Compose is a tool that helps you define and manage multi-container Docker applications. This guide covers installing Docker Compose on Linux and Windows.

---

## Install Docker Compose on Linux

### 1. Download Docker Compose
Run the following command to download Docker Compose:

```sh
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

### 2. Apply Executable Permissions

```sh
sudo chmod +x /usr/local/bin/docker-compose
```

### 3. Verify Installation

```sh
docker-compose --version
```

---

## Install Docker Compose on Windows

Docker Compose comes pre-installed with Docker Desktop for Windows. To install Docker Desktop:

### 1. Download Docker Desktop
Visit [Docker Desktop for Windows](https://docs.docker.com/desktop/setup/install/windows-install/) and download the installer.

### 2. Run the Installer
Double-click the downloaded `.exe` file and follow the installation wizard.

### 3. Verify Installation
Once installed, open PowerShell and run:

```sh
docker-compose --version
```

---

## Conclusion

Docker Compose simplifies running multi-container applications. Follow these steps to install it on your operating system and start managing containers efficiently!