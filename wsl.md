Installing Linux on Windows with WSL

Detailed instructions can be accessed directly from [Microsoft](https://learn.microsoft.com/en-us/windows/wsl/install).

# Install Windows Terminal

Downlod and install [Windows Terminal](https://apps.microsoft.com/detail/9n0dx20hk701?hl=en-US&gl=US). 

Windows Terminal offers a better tab management, GPU-accelerated performance, and rich customization than default cmd.exe PowerShell, or basic WSL terminals. It supports Unicode, smooth copy-paste, and split panes, making WSL feel more like a native Linux terminal.

# Install WSL command

Open PowerShell or Windows Command Prompt in administrator mode by right-clicking and selecting "Run as administrator" in terminal.

Run the command:

```
wsl --install -d Ubuntu-24.04
```


Ubuntu 24.04 LTS is a better choice than the default WSL Ubuntu because it receives long-term support (updates until 2029), ensuring stability and security patches.

# 

# Ypdate packages

```
sudo apt update && sudo apt upgrade -y
```

