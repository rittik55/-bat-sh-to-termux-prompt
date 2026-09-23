# Ritik-Hybrib-rom-flasher

Termux Rom file Extracter And Automatic Flashing command

2 - From Termux command line:
```bash
termux-setup-storage
```
```bash
curl -fsSL https://raw.githubusercontent.com/rittik55/Rittik-Hybrib-rom-flasher/main/rittikinstall.sh | bash
```

# 📱 PC Fastboot Script (.bat / .sh) to Termux Converter

Convert any PC Fastboot flashing script (`.bat`, `.cmd`, or `.sh`) into a 100% working **Termux-compatible Shell Script** using AI. 

Works with all custom ROMs and Android devices including **Redmi, Poco, Xiaomi, Realme, OnePlus, Motorola**, and more!

---

## 📋 Master AI Prompt

Copy the entire prompt below and send it to **Gemini**, **ChatGPT**, or **Claude** along with your PC `.bat` / `.sh` script:

```text
You are an expert Android Shell Script Developer and Fastboot Specialist.

My Task: I will provide you with a Windows Batch script (.bat / .cmd) or a Standard Linux Shell Script (.sh) below.

Your Objective:
1. Analyze the script and convert it into a fully functional Termux (Android) compatible Bash/Shell Script (.sh).
2. Fastboot Binary Handling:
   - Check if 'termux-fastboot' is available.
   - If not, fallback to system 'fastboot' or a local binary ('./bin/linux/fastboot').
3. Remove PC-Specific Commands:
   - Convert Windows-specific commands like `pause`, `cls`, `echo.`, `%~dp0`, `timeout`, etc., into Linux/Termux equivalents (e.g., `read`, `clear`, `cd "$(dirname "$0")"`).
4. Safety & Device Verification:
   - Retain or add a device codename check using `fastboot getvar product`.
   - If the connected device product name does not match the target device, halt execution immediately (exit 1) with an error message.
   - Add a data wipe / internal storage formatting warning with a required Y/N prompt confirmation from the user.
5. Flashing Logic Preservation:
   - Strictly preserve the original flashing sequence (`fastboot flash ...`, `set_active`, `erase`, `oem`).
   - Ensure all image file paths match the standard Termux directory layout (e.g., 'images/filename.img').
6. UI Layout:
   - Add a clean ASCII Header Banner at the top displaying the Author Name and Tool Name.

Here is my PC / Windows script:
--------------------------------------------------
[PASTE YOUR PC .BAT OR .SH CODE HERE]
--------------------------------------------------

Please generate a clean, error-free, and production-ready Termux Shell Script (.sh) only.
