# rk918-fw
This repository is for the RK ROYAL KLUDGE RK918/RK919 US ANSI layout firmware updater. If you're having any issues related to installing the wrong firmware on your board, then this would help.

# DISCLAIMER
I am not responsible if you flash this firmware onto a completely different keyboard and brick your keyboard.

# Information
The RK918 and RK919 share the same PCB and features, as the RK918 is a slight modification of the original RK919 PCB. The MCU running in these boards is a Huafenda HFD2201KBA. Doing research on this chip, it's been revealed that this is a rebranded version of a Sonix SN32F248B. Both of these boards share the same Vendor ID/Product ID (0c45:8006) as well as an older RK61 model. Using the RK61/RK919 software both work on each other for lighting configurations, although the RK61 software lacks of side lighting which is present on the RK918/RK919.

# Firmware update using ISP mode
If you ever come towards a situation where using the firmware updater tool doesn't function, it may be due to the lack of a VID/PID depending on what firmware you flashed the board with. The firmware updater for most HFD keyboards only detect based off of VID. Luckily the RK918 comes with a ISP (In-System Programming) function on the PCB. The keyboard requires 15 Philips head screws to disassemble the keyboard. One you've disassembled the board, you'll notice two chips. To determine the MCU location on the keyboard, it is usually the largest chip on the board. Any other chip may be an LED driver. Upon further inspection, you'll notice two pads by the MCU. 

<img width="678" height="915" alt="image" src="https://github.com/user-attachments/assets/19c3e355-4af0-4e87-a40b-88c3eb6daf6a" />

These are the pads used to enter bootloader mode if you're in a situation where using the firmware updater tool standalone doesn't work at all, then this would be important in recovering the keyboard.
Use a bent paper clip to short the two pads while the keyboard is unplugged. Plug in your keyboard while the pins are still being shorted. If you don't see any lighting, and the keyboard shows up as 0c45:7040 as it's VID/PID, then congratulations. You're now in bootloader mode. Extract and run the firmware updater, then wait for several seconds until you hear a disconnect/reconnect sound with the keyboard lighting up. You now have a working keyboard running on it's original firmware.
