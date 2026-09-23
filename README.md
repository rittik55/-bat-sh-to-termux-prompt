
# 📱 PC Fastboot Script (.bat / .sh) to Termux Converter

Convert any PC Fastboot flashing script (`.bat`, `.cmd`, or `.sh`) into a 100% working **Termux-compatible Shell Script** using AI. 

Works with all custom ROMs and Android devices including **Redmi, Poco, Xiaomi, Realme, OnePlus, Motorola**, and more!

---

## 📋 Master AI PPC Script convert to Termux Script Prompt

Copy the entire prompt below and send it to **Gemini**, **ChatGPT**, or **Claude** along with your PC `.bat` / `.sh` script:

```text
Act as an expert Fastboot Shell Script Generator. Convert the provided Windows Fastboot script (.bat / .cmd) or Linux script (.sh) into a clean, executable Termux shell script (.sh) following Ritik's Architecture.

CRITICAL FORMATTING & NO-SPAN RULES:
1. STRICTLY NO SPAN OR CITATION TAGS:
   - DO NOT include any HTML tags, span tags, citations, or markers like `[span_x]`, `(start_span)`, or `(end_span)` anywhere inside the code block.
   - Output MUST contain ONLY 100% pure executable shell code.

2. PURE CODE BLOCK ONLY:
   - Do NOT wrap the code in `cat << 'EOF'` or any file creation commands.
   - Do NOT include any conversational intro/outro text outside the code block.
   - Output exactly ONE single markdown bash code block suitable for direct 1-click copy into MT Manager or Text Editor.

3. RITIK'S ARCHITECTURE & RULES:
   - Line 1 & 2 Shebang and Directory Lock:
     #!/data/data/com.termux/files/usr/bin/sh
     cd "$(dirname "$0")" || exit 1

   - Fastboot Binary Auto-Detection:
     if command -v termux-fastboot >/dev/null 2>&1; then
         fastboot="termux-fastboot"
     elif command -v fastboot >/dev/null 2>&1; then
         fastboot="fastboot"
     elif [ -f "./bin/linux/fastboot" ]; then
         fastboot="./bin/linux/fastboot"
     else
         fastboot="fastboot"
     fi

   - ASCII Banner & Metadata:
     Display ASCII Banner with "MADE BY RITIK" and target device codename.

   - Device Verification:
     Check `device=$($fastboot getvar product 2>&1 | grep -F "product:" | tr -s " " | cut -d " " -f 2)`
     If mismatched with target device, print error and `exit 1`.

   - User Confirmation Prompt:
     Prompt `printf "Do you agree? (Y/N) "` and `read -r choice`. Exit if not 'y' or 'Y'.

   - Flashing Commands:
     Convert backslashes (`\`) to forward slashes (`/`).
     Use `$fastboot flash ...` line-by-line preserving exact partition order.

Convert this script now:
--------------------------------------------------
[PASTE YOUR .BAT OR .SH SCRIPT HERE]
--------------------------------------------------
