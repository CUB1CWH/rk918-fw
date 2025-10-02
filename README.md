# RK ROYAL KLUDGE RK918/RK919 Firmware Updater
<img width="608" height="299" alt="RK logo" src="https://github.com/user-attachments/assets/83d8b9ba-e7b4-42c5-8fbf-0f21acc5d433" />

This repository is for the RK ROYAL KLUDGE RK918/RK919 US ANSI layout firmware updater. If you're having any issues related to installing the wrong firmware on your board, then this would help.

# DISCLAIMER
I am not responsible for any damage or bricking that occurs if this firmware is used on an incompatible keyboard. Use at your own risk.

# Information
The RK918 and RK919 share the same PCB and features. The RK918 is a slight revision of the original RK919 PCB.

The MCU on these boards is a Huafenda HFD2201KBA, which is a rebranded Sonix SN32F248B microcontroller. These microcontrollers run off of the 32-bit ARM-Cortex M0 architecture. You can find the data sheet here: https://www.sonix.com.tw/article-en-4336-30356

The bootloader on these keyboards are unbrickable, as the bootloader on these chips are stored in ROM (Read-Only Memory) on the MCU. Even if you flash a completely incompatible firmware on the board, the keyboard will still light up partially in different areas or play a connect sound once you plug it in.

<img width="729" height="218" alt="image" src="https://github.com/user-attachments/assets/e6767567-a077-451c-9f93-81fb6330a028" />

Both boards share the same Vendor ID/Product ID (0C45:8006), also used by older RK61 models.

The RK61 software can be used for lighting configurations on the RK918/RK919, though it lacks support for side lighting present on the RK918/RK919.

# Firmware update using ISP mode

<img width="542" height="293" alt="image" src="https://github.com/user-attachments/assets/34c22e54-d9d5-4ed8-acf6-4b0e433e74e9" />

In some cases, the firmware updater may fail to detect your keyboard. This is often due to a missing or incorrect VID/PID, depending on the firmware currently installed. The firmware updater for most HFD keyboards only detect based off of VID (0c45). Luckily the RK918 features an In-System Programming (ISP) mode, which allows direct firmware flashing even when the updater does not detect the device automatically. The board requires 15 Philips head screws to disassemble the keyboard. One you've disassembled the board, you'll notice two chips. To determine the MCU location on the keyboard, it's typically the largest chip on the board. Any other chip may be an LED driver (HFD9901LIA). Next to the MCU, you will find two small pads.

<img width="678" height="915" alt="image" src="https://github.com/user-attachments/assets/19c3e355-4af0-4e87-a40b-88c3eb6daf6a" />

These pads are used to enter bootloader mode, which is important if the firmware updater tool cannot detect the keyboard. To use them:

With the keyboard unplugged, short the two pads using a bent paper clip or similar tool.

While keeping the pads shorted, plug in the keyboard.

If no lighting appears and the keyboard is detected with a VID/PID of 0C45:7040, then congratulations. You are now in bootloader mode. Safely remove the paper clip off of the pads.

Extract and run the firmware updater. Wait several seconds until you hear the disconnect/reconnect sound and see the keyboard powering on with side lighting and a ripple effect as shown below:

![RK918 boot compressed](https://github.com/user-attachments/assets/ca631e79-af68-4146-8e9c-036fecca397c)

Your keyboard is now restored and running its original firmware.
