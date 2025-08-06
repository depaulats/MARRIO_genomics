Installing Linux on Windows with WSL

Detailed instructions can be accessed directly from [Microsoft](https://learn.microsoft.com/en-us/windows/wsl/install).

# Install Windows Terminal

Downlod and install [Windows Terminal](https://apps.microsoft.com/detail/9n0dx20hk701?hl=en-US&gl=US). 

Windows Terminal offers a better tab management, GPU-accelerated performance, and rich customization than default cmd.exe PowerShell, or basic WSL terminals. It supports Unicode, smooth copy-paste, and split panes, making WSL feel more like a native Linux terminal.

# Install WSL

Open PowerShell or Windows Command Prompt in administrator mode by right-clicking and selecting "Run as administrator" in terminal.

Run the command:

```
wsl --install -d Ubuntu-24.04
```

You can chnage the Linux distro with the `-d` option. WE suggest using Ubuntu 24.04 LTS over the default WSL Ubuntu because it receives long-term support (updates until 2029), ensuring stability and security patches.

# Set up your Linux user info

When you open Ubuntu after installation, you will be prompted to create a user account and password for your. Have in mind that you will have to type your password everytime you do a command as a super user (´sudo`), so keep it close and avoid extra complicated paswords. 

# Update packages

As a first step 

After installing Linux on WSL make sure you get the latest security patches, bug fixes, and software improvements to keep your system stable and secure by running:

```
sudo apt update && sudo apt upgrade -y
```

Remember to run this command periodically.

# Installing an environment manager.

You are now set to dive into the [tutorials](https://github.com/depaulats/MARRIO_genomics/blob/main/tutorials.md).

