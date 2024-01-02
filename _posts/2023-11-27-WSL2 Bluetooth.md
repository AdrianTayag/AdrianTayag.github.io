---
layout: post
title: "Learn: Sharing Bluetooth devices for use inside WSL2"
categories: guide, devtools
---
### Pre-requisites
1. USBIPD - https://github.com/dorssel/usbipd-win
2. WSL2 Installed (Ubuntu)
3. Supported bluetooth device (Tested on Intel AX200)
4. Backup of your current WSL2 (Just in case)
5. Build-essentials
6. Patience (during kernel build)

### Steps
1. Update Kernel
2. Install bluetooth libraries
3. Pass in bluetooth device
4. Start bluetooth services
5. Enjoy!

### Resources
- Installing WSL2: https://learn.microsoft.com/en-us/windows/wsl/install
- Updating Kernel to V6.X: https://learn.microsoft.com/en-us/community/content/wsl-user-msft-kernel-v6
- Discussion on usb-ipd repo: https://github.com/dorssel/usbipd-win/discussions/310