---
layout: post
title: "Learn: Sharing Bluetooth devices for use inside WSL2"
categories: guide, devtools
---
### Introduction
This short writeup summarizes my experience in enabling bluetooth device pass through for WSL2 usage. In the future, newer WSL kernels may support this feature out of the box and this guide may get outdated.

### Pre-requisites
1. WSL2 running on your device
2. USBIPD - https://github.com/dorssel/usbipd-win
3. Supported bluetooth device (Tested on Intel AX200)
4. Backup of your current WSL2 (Just in case things go wrong)

### Steps
1. Update Kernel
    Follow this guide until step 4, right before building the kernel (since we will need to modify the configurations before continuing)
2. Install bluetooth libraries via menuconfig
    > via your Terminal:
    ![Menuconfig_entry](/assets/wsl2_bluetooth/menuconfig_entry.PNG)

    > Select Networking Support via pressing Enter:
    ![Menuconfig_0](/assets/wsl2_bluetooth/menuconfig_0.PNG)

    > Enable Bluetooth subsystem support via pressing Y:
    ![Menuconfig_1](/assets/wsl2_bluetooth/menuconfig_1.PNG)

    > Enable the relevant Bluetooth support as follows:
    ![Menuconfig_2](/assets/wsl2_bluetooth/menuconfig_2.PNG)

    > Go to Bluetooth device drivers (last entry) and enable the following:
    ![Menuconfig_3](/assets/wsl2_bluetooth/menuconfig_3.PNG)

    > Continue following the Microsoft guide until the end. NOTE: Building the kernel will take a few minutes depending on your system. 

3. Pass in bluetooth device
    > sudo apt update   
    > sudo apt install bluez dbus  
    > echo 'export BLUETOOTH_ENABLED=1' | sudo tee /etc/default/bluetooth  

4. Start bluetooth services
    > sudo service dbus start  
    > sudo service bluetooth start  
    > bluetoothctl  
    > scan on  

    ![bluetooth_usage](/assets/wsl2_bluetooth/bluetoothctl.PNG)
5. Enjoy!
    For my use case, I am using it to commission Matter devices via the [CHIP Tool](https://project-chip.github.io/connectedhomeip-doc/guides/chip_tool_guide.html).

    ![chip-tool](/assets/wsl2_bluetooth/chip-tool.PNG)

### Resources
- Installing WSL2: https://learn.microsoft.com/en-us/windows/wsl/install
- Updating Kernel to V6.X: https://learn.microsoft.com/en-us/community/content/wsl-user-msft-kernel-v6
- Discussion on usb-ipd repo: https://github.com/dorssel/usbipd-win/discussions/310
