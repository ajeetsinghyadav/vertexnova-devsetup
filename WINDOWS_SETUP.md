# 🪟 VertexNova — Windows Setup Guide

This guide helps set up a developer-friendly Windows environment for building and working on the VertexNova project.

---

## 🍫 Chocolatey Setup (Recommended)

Chocolatey is a package manager for Windows that makes installing CLI tools and utilities easy and scriptable.

### Install Chocolatey

Open PowerShell as Administrator and run:
```
Set-ExecutionPolicy Bypass -Scope Process -Force; \
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; \
iwr https://community.chocolatey.org/install.ps1 -UseBasicParsing | iex
```

---

## 📦 Essential Development Tools for VertexNova

### 🔧 Core Build & Development Tools

- **Install [Visual Studio 2022 Community](https://visualstudio.microsoft.com/vs/community/)**
  - During installation, select:
    - Desktop development with C++
    - C++ CMake tools for Windows
    - Windows 10/11 SDK
    - Git for Windows

- For all other tools, use Chocolatey:
```
choco install -y cmake ninja git python 7zip curl wget ripgrep fd bat neovim
```

- For PowerShell 7, Windows Terminal, and Oh My Posh:
```
choco install -y powershell oh-my-posh microsoft-windows-terminal
```

- For htop, ranger, and trash-cli, use MSYS2 or WSL as these are not natively available via Chocolatey.

- **Install [GDB for Windows](https://www.msys2.org/)** (via MSYS2, optional)

---

## 🐍 Python Environment

- Python is installed via Chocolatey above. To set up a virtual environment:
```
python -m pip install --upgrade pip
python -m pip install virtualenv
```

---

## 🧵 Shell / Terminal Enhancements

- Use Windows Terminal and PowerShell 7 (installed via Chocolatey).
- Configure Oh My Posh for prompt customization. See [Oh My Posh docs](https://ohmyposh.dev/docs/installation/windows).

---

## 🧐 Productivity CLI Tools

- All major CLI tools (ripgrep, fd, bat, neovim, etc.) are installed via Chocolatey above.
- For advanced tools (htop, ranger, trash-cli), use MSYS2 or WSL.

---

## 🎮 Vulkan SDK (Windows)

Install the official Vulkan SDK (includes headers, libraries, validation layers, and tools):

```
choco install -y vulkan-sdk
```

Notes:
- The installer sets the `VULKAN_SDK` environment variable and updates `PATH` for tools like `vulkaninfo` and `glslangValidator`.
- For the latest releases and manual installer, see `https://vulkan.lunarg.com/sdk/home`.

---

## 📚 Doxygen (Documentation)

Install Doxygen and Graphviz for documentation generation:

```
choco install -y doxygen.install graphviz
```

After installation, restart your terminal so PATH updates are picked up.

---

## 🧰 Install Visual Studio Code

```
choco install -y vscode
```

---

## 🧱 Install MeshLab

- Download and install from [https://www.meshlab.net/#download](https://www.meshlab.net/#download)

---

## 🌟 Done

Your Windows system is now ready for working on VertexNova!
