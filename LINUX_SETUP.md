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

## 🎮 Vulkan SDK and Tools

Install Vulkan development headers, validation layers, tools, and SPIR-V toolchain:

```
sudo apt install -y \
  libvulkan-dev \
  vulkan-tools \
  vulkan-validationlayers-dev \
  spirv-tools \
  glslang-tools \
  shaderc \
  spirv-headers
```

Optional: Install the latest official Vulkan SDK from LunarG (provides samples, layers, docs). See `https://vulkan.lunarg.com/sdk/home` for the most recent version and Linux installation instructions.

```
# Example (replace VERSION with the latest, e.g., 1.3.296.0):
wget https://sdk.lunarg.com/sdk/download/VERSION/linux/vulkan_sdk.tar.gz -O vulkan_sdk.tar.gz
mkdir -p $HOME/.local/vulkan-sdk && tar -xzf vulkan_sdk.tar.gz -C $HOME/.local/vulkan-sdk --strip-components=1
echo 'export VULKAN_SDK="$HOME/.local/vulkan-sdk/x86_64"' >> ~/.bashrc
echo 'export PATH="$VULKAN_SDK/bin:$PATH"' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH="$VULKAN_SDK/lib:$LD_LIBRARY_PATH"' >> ~/.bashrc
echo 'export VK_LAYER_PATH="$VULKAN_SDK/etc/vulkan/explicit_layer.d"' >> ~/.bashrc
```

Reload your shell configuration if needed.

```
source ~/.bashrc or source ~/.zshrc
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

## 📚 Doxygen (Documentation)

Install Doxygen and Graphviz for generating code documentation:

```
sudo apt install -y doxygen graphviz
```

## 🧐 Productivity CLI Tools

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

## 🧵 Shell Setup — Zsh + Oh My Zsh

```
sudo apt install -y zsh
```

### 🚀 Install Oh My Zsh

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 🔧 Plugins
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

### 🌟 Enable Plugins

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

### 🌈 Optional: Powerlevel10k Theme

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

### 🚧 Useful Aliases

Append to ~/.zshrc:

```
alias cp="rsync -avhW --no-compress --progress --info=progress2"
alias cat="bat"
alias find="fd"
```

### 💪 Make Zsh the Default Shell

```
chsh -s $(which zsh)
```

---

## 🧰 Install Visual Studio Code

Download the latest .deb package from the official website:

```
wget https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64 -O vscode.deb
sudo apt install ./vscode.deb
```

Alternatively, install via Snap:

```
sudo snap install code --classic
```

---

## 🧱 Install MeshLab

```
sudo apt install -y meshlab
```
---

## 🔄 Configure Multiple GCC/G++ Versions

Install specific versions (e.g., GCC 11 and GCC 13):

```
sudo apt install -y gcc-11 g++-11 gcc-13 g++-13
```

Set up alternatives:
```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 110
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-13 130
```

```
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-11 110
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-13 130
````
Choose default version:

```
sudo update-alternatives --config gcc
sudo update-alternatives --config g++
```

Verify:

```
gcc --version
g++ --version
```
---

## 🌟 Done

Your system is now ready for working on VertexNova!

