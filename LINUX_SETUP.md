# 🐧 VertexNova — Linux Setup Guide (Ubuntu 24.04+)

This guide helps set up an efficient and developer-friendly Linux environment for building and working on the VertexNova project and other software projects.

---

## 🔄 System Update

```bash
sudo apt update && sudo apt upgrade

## 📦 Essential Development Tools for VertexNova

This section installs all core development, CLI, and graphics tools needed to build and work with the VertexNova engine on Ubuntu 24.04+.

---

### 🔧 Core Build & Development Tools

```bash
sudo apt install -y \
  build-essential \
  cmake-qt-gui \
  g++ \
  gdb \
  git \
  binutils \
  ninja-build \
  pkg-config \
  autoconf \
  automake \
  libtool \
  libtool-bin \
  unzip

