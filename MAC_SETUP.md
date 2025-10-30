# 🍏 VertexNova — macOS Setup Guide

This guide helps set up an efficient and developer-friendly macOS environment for building and working on the VertexNova project.

---

## 🔄 System Update

- Update macOS via **System Settings > General > Software Update**.

## 📦 Essential Development Tools for VertexNova

### 🔧 Core Build & Development Tools

- **Install [Xcode](https://developer.apple.com/xcode/)** from the App Store
- Install Xcode command line tools:
  ```
  xcode-select --install
  ```
- **Install [Homebrew](https://brew.sh/):**
  ```
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
- Install core tools:
  ```
  brew install cmake ninja git gdb autoconf automake libtool unzip pkg-config
  ```

## 🖼️ OpenGL / Qt / Graphics Development Libraries

```
brew install qt gettext
```

## 🎮 Vulkan SDK and MoltenVK (macOS)

On macOS, Vulkan runs via Metal using MoltenVK. Install the Khronos Vulkan SDK and MoltenVK:

```
brew install --cask vulkan-sdk
brew install molten-vk
```

Notes:
- The SDK provides headers, validation layers, `glslangValidator`, `spirv-tools`, and samples.
- MoltenVK implements Vulkan over Metal. Ensure `VK_ICD_FILENAMES` and other environment variables are configured if needed by your build system.
- For latest release notes and manual installers, see `https://vulkan.lunarg.com/sdk/home`.

Verify tools:

```
vulkaninfo || echo "Install VK tools or ensure PATH includes Vulkan SDK bin"
```

## 🐍 Python Environment

```
brew install python
python3 -m pip install --upgrade pip
python3 -m pip install virtualenv
```

## 📦 Compression & Networking Utilities

```
brew install curl wget unrar
```

## 🧵 Shell / Terminal Enhancements

```
brew install zsh mc
```

## 📚 Doxygen (Documentation)

Install Doxygen and Graphviz for documentation generation:

```
brew install doxygen graphviz
```

## 🧐 Productivity CLI Tools

```
brew install htop ripgrep fd bat neovim ranger trash
```

## 🧱 Terminal Setup — iTerm2 (Optional)

- Download and install [iTerm2](https://iterm2.com/)

## 🧵 Shell Setup — Zsh + Oh My Zsh

- Zsh is the default shell on macOS. Install Oh My Zsh:
  ```
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
  ```
- Install plugins:
  ```
  git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
  git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
  git clone https://github.com/MichaelAquilina/zsh-you-should-use.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/you-should-use
  git clone --recursive --depth 1 https://github.com/mattmc3/zsh-safe-rm.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-safe-rm
  ```
- Edit `~/.zshrc` to enable plugins:
  ```
  plugins=(git zsh-autosuggestions zsh-syntax-highlighting you-should-use zsh-safe-rm)
  source ~/.zshrc
  ```
- (Optional) Install Powerlevel10k theme:
  ```
  git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
  ```
  In `~/.zshrc`:
  ```
  ZSH_THEME="powerlevel10k/powerlevel10k"
  ```
  Then run:
  ```
  exec zsh
  p10k configure
  ```
- Useful aliases (append to `~/.zshrc`):
  ```
  alias cp="rsync -avhW --no-compress --progress --info=progress2"
  alias cat="bat"
  alias find="fd"
  ```
- Make Zsh the default shell:
  ```
  chsh -s $(which zsh)
  ```

## 🧰 Install Visual Studio Code

- Download and install from [https://code.visualstudio.com/](https://code.visualstudio.com/)

## 🧱 Install MeshLab

```
brew install --cask meshlab
```

## 🔄 Configure Multiple GCC/G++ Versions

```
brew install gcc@11 gcc@13
```
- Use Homebrew's `brew link` to switch between versions as needed.

## 🌟 Done

Your macOS system is now ready for working on VertexNova!
