# 🐧 VertexNova — Linux Setup Guide (Ubuntu 24.04+)

This guide helps set up an efficient and developer-friendly Linux environment for building and working on the VertexNova project and other software projects.

---

## 🔄 System Update

```
sudo apt update && sudo apt upgrade
```

## 📦 Essential Development Tools for VertexNova

This section installs all core development, CLI, and graphics tools needed to build and work with the VertexNova engine on Ubuntu 24.04+.

---

### 🔧 Core Build & Development Tools

```
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
```
## 🖼️ OpenGL / Qt / Graphics Development Libraries

```
sudo apt install -y \
  mesa-common-dev \
  libglu1-mesa-dev \
  extra-cmake-modules \
  gettext
```

## 🐍 Python Environment

```
sudo apt install -y \
  python3-pip \
  python3-virtualenv
```

## 📦 Compression & Networking Utilities

```
sudo apt install -y \
  curl \
  wget \
  rar \
  unrar
```
## 🧵 Shell / Terminal Enhancements

```
sudo apt install -y \
  zsh \
  mc \
  preload
```

🧐 Productivity CLI Tools

```
sudo apt install -y \
  htop \
  ripgrep \
  fd-find \
  bat \
  neovim \
  ranger \
  trash-cli
```

bat installs as batcat and fd-find as fdfind.

```
ln -s $(which batcat) ~/.local/bin/bat
ln -s $(which fdfind) ~/.local/bin/fd
```

## 🪟 Wayland & X11 Dependencies

```
sudo apt install -y \
  wayland-protocols \
  wayland-scanner++ \
  libwayland-dev \
  libx11-dev \
  libxrandr-dev \
  libxinerama-dev \
  libxcursor-dev \
  libxi-dev
```
---

## 🧱 Terminal Setup — Terminator

Terminator is a tiling terminal emulator that supports multiple panes and tabs.

### 📥 Install Terminator

```
sudo apt install -y terminator
```

🧵 Shell Setup — Zsh + Oh My Zsh

```
sudo apt install -y zsh
```

🚀 Install Oh My Zsh

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

🔧 Plugins
```

git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

```
git clone https://github.com/MichaelAquilina/zsh-you-should-use.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/you-should-use
```

```
git clone --recursive --depth 1 https://github.com/mattmc3/zsh-safe-rm.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-safe-rm
```

🌟 Enable Plugins

Edit ~/.zshrc:

```
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
  you-should-use
  zsh-safe-rm
)
```

```
source ~/.zshrc
```

🌈 Optional: Powerlevel10k Theme

```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

```
In ~/.zshrc:

```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Then run:
```
exec zsh
p10k configure
```

🚧 Useful Aliases

Append to ~/.zshrc:

```
alias cp="rsync -avhW --no-compress --progress --info=progress2"
alias cat="bat"
alias find="fd"
```

💪 Make Zsh the Default Shell

```
chsh -s $(which zsh)
```

🌟 Done

Your system is now ready for C++/Qt/OpenGL development and working on VertexNova!

