---
name: pc-black-screen-issue
description: "User's ASUS ROG desktop has recurring black screens and hard crashes; troubleshooting in progress as of July 2026"
metadata: 
  node_type: memory
  type: project
  originSessionId: 728d1e08-ca6f-4eb3-8a92-7b3ccd62065b
---

User's PC: ASUS ROG G700TF desktop, Windows 11 Home, NVIDIA RTX 5060, two Samsung monitors (LS27D36xG + C27F390, both 1080p over HDMI).

**Problem (as of 2026-07-02):** Screens go black every few minutes during active use, plus 8 hard power-loss shutdowns (Kernel-Power 41, mostly no crash dump) between 2026-06-20 and 2026-07-02, clustered around 8–9 AM. One bugcheck 0x139 KERNEL_SECURITY_CHECK_FAILURE on 2026-06-25 (dump: C:\Windows\Minidump\062526-18734-01.dmp).

**Ruled out:** cables and HDMI ports (user swapped both), power/screensaver settings, GPU driver TDR resets (none logged), DWM crashes, monitor PnP disconnect events, GPU temps (44°C idle).

**Done on 2026-07-02:** updated NVIDIA driver 591.86 → 610.62 (via NVIDIA App; standalone installer was blocked by Bitdefender when run from Temp). Ran NVIDIA UEFI Firmware Updater 2.0 — GPU reported "Already updated," so the RTX 5060 vBIOS black-screen fix was already applied; firmware ruled out.

Windows Memory Diagnostic run 2026-07-02: **passed, no errors** (standard pass; MemTest86 overnight would be more exhaustive if needed).

**Update 2026-07-03:** Hard crashes appear FIXED by the 610.62 driver — first 28-hour stretch with no Kernel-Power 41 after 8 crashes in 2 weeks. Black screens persist (4x in 10 min), still zero log traces, GPU healthy. User confirmed **only ONE monitor goes black** (not both, PC stays responsive) → problem is monitor-side, not the PC. User unsure which monitor; asked them to note left vs right next occurrence.

**Update 2026-07-03 (later):** Blacking-out monitor identified = RIGHT = **Samsung Odyssey LS27D36xG** (DISPLAY2, was 100Hz; left monitor C27F390 is DISPLAY1 @ 60Hz, never fails). Dropped Odyssey to 60Hz AND replaced cable — **still blacks out**. Every external cause now eliminated: cable (replaced), port (swapped), bandwidth (60Hz), GPU driver/firmware (updated/current), GPU hardware (left monitor on same GPU is fine). **Conclusion: the Odyssey LS27D36xG hardware is faulty (power/T-CON board).**

**MAJOR REVISION 2026-07-08 — it's a POWER/HARDWARE fault, not (just) the monitor:**
- Black screens now occur on BOTH monitors simultaneously (was reported as right-only on 7/3; has progressed or was incomplete). GPU browns out and recovers; still nothing logged.
- Hard crashes did NOT stop — another Kernel-Power 41 on 7/7 8:11 AM. Driver update only reduced frequency (1 in 5 days vs daily).
- ALL 9 crashes = BugcheckCode 0 (pure power loss / hard freeze, no dump). Occasional stray bugchecks (313/340/122) inconsistent = unstable hardware, not one driver bug.
- **Trigger identified: crashes happen within ~3 min of resuming from S3 sleep, in the morning.** 7/7: resumed 8:08 AM → dead 8:11 AM. Classic "PSU weak when cold / on power-state transition" signature.
- Ruled out: RAM (passed), thermals (45C), WHEA (none), driver TDR (none), monitor cable/port/refresh.
- **Leading suspect: failing/marginal PSU (or GPU power delivery).** Machine also wakes hourly overnight (wake timers / RemoteConnection), multiplying risky resume transitions.

**Hardware details (7/8):** Motherboard ASUS B860M MAX GAMING AX (inside ROG G700TF prebuilt). BIOS = 9020, dated 8/28/2025 (OEM version numbering). Latest retail BIOS = 3021, 5/28/2026 (notes: improved stability, Intel ME firmware update, CPU microcode update). PC is on a CyberPower CP1500PFCLCD pure-sinewave UPS w/ AVR (clean input power — rules out wall power; UPS NOT connected via USB so no PowerPanel logging). Armoury Crate IS installed.

**VERDICT 2026-07-10 (evening): HARDWARE CONFIRMED.** Black screens recurred same day the full BIOS 9043 + ME 19.0.5.2175 stack went live. Decision point reached → ASUS warranty, no more DIY. Serial: TAPFAG01149843C. ASUS US: 1-812-282-2787 / asus.com/us/support RMA. Warranty script saved in chat 7/10: hard power-off crashes (Kernel-Power 41, BugcheckCode 0, 9x in 3 weeks, mostly on resume-from-sleep) + all-day both-monitor blackouts; all firmware/drivers current; RAM/temps/UPS/cables/monitors ruled out; points at PSU/power delivery.

**OLD PLAN 2026-07-08 (completed):**
1. **BIOS update: FULLY DONE 2026-07-10.** Flashed 9020 → **9043** via EZ Flash from USB, then second EZ Flash pass with the full ZIP to apply **Intel ME firmware 19.0.5.1992 → 19.0.5.2175** (EZ Flash only auto-updates ME when you select the ZIP, not the .CAP; also: must double-click the file, not just highlight the drive). File from ASUS download API https://dlcdnets.asus.com/pub/ASUS/GamingDT/G700TF/G700TF.9043.zip, SHA-256 verified 301C793A…. Business files backed up to G:\My Drive\PC-Backup-2026-07-10 first. **ALL software/firmware layers now current: GPU driver 610.62, GPU vBIOS, BIOS 9043, ME 19.0.5.2175.** If black screens/crashes persist → hardware confirmed → ASUS warranty, no more DIY.
2. BACK UP DATA — repeated hard power loss can corrupt Windows/files.
3. If crashes/brownouts persist AFTER latest BIOS → confirmed hardware power fault → ASUS warranty (describe: hard power-off reboots on resume-from-sleep, Kernel-Power 41 BugcheckCode 0 no dump, both-monitor brownouts all day). Leading suspect internal PSU (motherboard fits worse — no POST/WHEA/port/CMOS signs).
4. Note: "turn off Windows animations" tip (YouTube) won't fix power-loss reboots — declined as a real fix.
5. Optional stopgap: disable sleep + wake timers to cut morning crashes. Fast Startup already OFF.
6. Monitor (Odyssey LS27D36xG) may have an independent issue but is NOT the cause of crashes/both-screen blackouts.

Note: Bitdefender is the active AV — it silently kills installers run from Temp folders; run installers from Downloads instead.
