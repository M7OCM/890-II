# Modified OEFWCOM Transceiver Firmware for Radtel RT-890

**890-II PCB 2.1 Only**

For old PCB 2.0 model see [here](https://github.com/M7OCM/890)

M7OCM v2.1.7+ PCB 2.1 Firmware based on Open Edition Firmware Community.

This is a personal project for my use primarily with emphasis on VHF/UHF airband monitoring. Unfortunately, I cannot accomodate feature requests due to time constraints - this is just a hobby I do for fun (joke). Its "as is". If you don't like it, or it doesn't perform to your expectations don't use it or join forces - fork your own version, modify mine or start from scratch; code freely available here:

[OEFWCOM](https://github.com/OEFW-community/RT-890-custom-firmware)

[DualTachyon OEFW UV-K5/RT-890](https://github.com/dualtachyon)

![20241030_163100](https://github.com/user-attachments/assets/4a0da61f-f4b3-433a-9019-71fe09716fea)

**LATEST**

23 November 2024 2 bin files: v2.2.4Q and v2.2.4X both for PCB2.1. Q = Spectrum Auto Light; X = Standard light always on. Both versions updated with newer widescreen spectrum and code clean.

![20241123_233645](https://github.com/user-attachments/assets/78b5f20b-e3f2-4b39-a51d-8349e1347d55)

v2.2.3Q PCB2.1 Spectrum Auto Light squelch. A good battery saver and for using the spectrum to monitor a range of channels such as the 16 PMR446 channels or the entire VHF Marine band at once. No delays faster than scanning same in memory. Read the instructions below for more info (**Spectrum**).

v2.2.3 PCB2.1 VHF filter returned to 240 MHz, ui dialog overlays fixed

v2.2.2 PCB2.1 VHF filter range choice - choose either bin 240 MHz or 280 MHz, ui various/menu renames, user interfacing - added functional stability, fixes, minor code clean up.

v2.2.1 PCB2.0 Dialog box size, position, less obtrusive.

v2.2.0 PCB2.1 Fast scan/search introduced, only change from previous version.

v2.1.9 PCB2.1 UI. Light theme colours changed. Some were hard to see when the radio was used outside (not perfect, but hey ho). Signal strength meter split into thirds rather than quarters. Single Freq mode: register display order changed to reflect AM Fix code order (LNAS, LNA, MIX, PGA). BW and WK are tunable separately and on boot are defaulted BW4 WK0, feel free to adjust in either AGC or FGC modes BW2 WK1 are good for fine tuning.

The register order change makes cross referencing the gain table (see Register Editor below) much easier, especially for users experimenting with FGC (AM Fix off).

AM Fix. I've been testing the previous changes I made exclusively for many weeks and I'm pleased with overall performance. There are times when gain fluctuates, noise spikes, and in some instances audio is truncated or quietens. That said for the relatively few instances where the auto gain response is inadequete the vast majority of time, overall listening pleasure is improved, use FGC if you are struggling, or open the squelch, wait a few seconds, to unleash max gain thus realigning AGC. Thats my finding anyway, your experience may well differ. Location and antenna type/gain play a major role in all of this. I've experimented with numerous antennae, but its nigh on impossible to cater for all eventualities - don't expect miracles!

EXPERIMENTAL releases (2)

v2.1.8 released. Remit: Improve AM. Changes made to chip default registers and improved AM Fix code specifically for the RT-890 PCB 2.1. AM Fix default "on", works well even with 20dB external gain, in fact the more gain the better results (IMO). Also works with AM Fix off, but may lead to overloading in some circumstances. Working on further mods to improve this. Possibly do away with AM Fix altogether (that's the goal).

27 June 2024 v2.1.7 released early with a provisio: early days using PCB 2.1 testing is not complete, work in progress - feel free to change parameters. 1 bin file to accommodate new PCB 2.1 revision - BK4819 GPIO0 (pin 28) has moved to GPIO3 (pin 31).

There are a lot of UI changes, plus the scan speed has been reduced to stock for stability (this can be increased, but at the expense of tone detection and search never stopping on a carrier in VFO mode. I have reverted to 890-I stock filter bandwidth ie 0x4048 : 0x3028 to improve performance for PCB 2.1 (PCB 2.0 version will be different) as it seems the 2.1 version is less sensitive on airband. Again this open to further testing and experiment. Other parts of the firmware will be looked into to try and improve that aspect. For now it works and is stable. I recommend using AM Fix on PCB 2.1. On a positive note AM is less likely to over saturate (from limited testing) with AM Fix off.

Thanks to Kevin @Radtel for the latest hardware for testing firmware compatibility.

[OEFWCOM](https://github.com/OEFW-community/RT-890-custom-firmware)

[DualTachyon OEFW UV-K5/RT-890](https://github.com/dualtachyon)

**Default Keys**

- Side Key [1SP] Monitor
- Side Key [1LP] Freq Detect
- Side Key [2SP] Scan/Advance Scan List/Scan Stop (LP)
- Side Key [2LP] Spectrum

SP = Short Press; LP = Long Press

The following keypad keys are all LP

- [1] Squelch
- [2] Modulation
- [3] Bandwidth
- [4] TX Power
- [5] AM Fix
- [6] Dual Watch
- [7] Repeater Mode
- [8] Reg Editor - RF Gain Control
- [9] Scan List Add or remove a channel to current scan list
- [0] FMB
- [*] Edit TX Freq
- [#] Lock
- [MENU] TX CTCSS/DCS
- [EXIT] Single/Dual Display

Side Key/Custom Key(pad) Options
- None
- Monitor
- Freq Detect
- Repeat Mode
- Preset Ch
- Local Alarm
- Remote Alarm
- NOAA
- Send Tone
- TX Tone
- FM Radio
- Freq Scanner
- Flashlight
- AM Fix
- VOX
- TX Power
- Squelch
- Dual Watch
- Backlight
- Freq Step
- Key Beep
- +/- Scan L#
- DTMF Input
- Dual Display
- TX Frequency
- Lock
- Spectrum
- Dark Theme
- RF Gain
- Reg Editor
- Mic Gain
- Modulation
- Bandwidth
- TX CTCSS/DCS
- TX Priority

**Spectrum**

Enter by pressing side key 2 LP

- [Up] Increase frequency range
- [Down] Decrease frequency range
- [1] Change scan step (16, 32, 64 or 128)
- [2] Backlight override SAL *("Q" versions only)*
- [3] Change modulation FM, AM or SB (SSB)
- [4] Change step size (0.25k - 50k)
- [5] Switch spectrum modes (toggle 1-4)
- [6] Increase squelch level
- [7] Hold/Search (in hold, use up/down to adjust main frequency - useful to avoid RFI)
- [9] Decrease squelch level
- [0] Toggle v/u band filter (F = On, X = Off)
- [*] Change scan delay (0 - 10ms)
- [#] Toggle bandwidth (25.0K = wide, 12.5K = narrow)
- [MENU] Jump to VFO mode with current frequency and bandwidth (to allow TX FM only)
- [EXIT] Return to main

SP [#] switch between VFO-CH mode

*Spectrum Auto Light (SAL) "Q" versions only - all other versions backlight is always on*

The squelch threshold determines the auto display lighting. In as much as when no signal is received the display will go off (technically the display LED is off, the screen itself is always on).

Firstly, find an appropriate squelch threshold above the noise level (Key 9). Increase it if need be by pressing Key 6 (even if screen is off).

If the screen light goes off after an incoming signal and you want to change a setting, short press Key 2 (once) to illuminate the display. The LED on top of the radio will be a steady orange (yellow-ish) colour when Key 2 is active. When a signal is received the spectrum screen will stay on for the duration of RX then extinguish. There is no delay timer to hasten response time (faster than scanning). When in RX mode the top LED is green. When the display is off, the top LED colour will also be off.

To keep the display illuminated longer increase squelch threshold.

Note, interference will also turn the display on. Solution, increase squelch threshold.

Scan Delay can be adjusted by Key [*] to prevent excessive screen flashing due to RFI, I'd suggest a value of 8+ if the default (4) is troublesome.

**Register Editor**

Press key 8 LP and Register Editor will launch, showing the current register values. The register currently being edited will display in large font.

- [Up] Move editor to next register
- [Down] Move to previous register
- [1] Change RF Gain Control (AGC 3, FGC 3/2/1/0/7/6/5/4); If AM Fix is on, use AGC 3 (default). Turn AM Fix off if using FGC
- [2] Decrease value of current register's setting by 1
- [3] Increase value of current register's setting by 1
- [EXIT] Return to main

AGC = Auto Gain Control. FGC = Fixed Gain Control.

FGC is a manual option - user selects parameters for fine tuning AM signals to prevent front end overloading.

- LNAS Coarse attenuator (short)
- LNA Fine tuning attenuator
- PGA Programmable threshold amplifier
- MIX Mixer gain
- BW Bandwidth filter 
- WK Weak signal threshold

AGC 3 Registers used in AM Fix, useful also in FGC mode to determine exact dB reduction/increase set.

Order is LNAS, LNA, MIX, PGA

- 0000 ... -98dB
- 0010 ... -96dB
- 1000 ... -95dB
- 0100 ... -93dB
- 0001 ... -92dB
- 0110 ... -91dB
- 0011 ... -90dB
- 1001 ... -89dB
- 0120 ... -88dB
- 1030 ... -87dB
- 0002 ... -86dB
- 1120 ... -85dB
- 0031 ... -84dB
- 0300 ... -83dB
- 1130 ... -82dB
- 1031 ... -81dB
- 0230 ... -80dB
- 1201 ... -79dB
- 0320 ... -78dB
- 1400 ... -77dB
- 1131 ... -76dB
- 0023 ... -75dB
- 1301 ... -74dB
- 1600 ... -73dB
- 0710 ... -72dB
- 0620 ... -71dB
- 2131 ... -70dB
- 0312 ... -69dB
- 0006 ... -68dB
- 0521 ... -67dB
- 0016 ... -66dB
- 1232 ... -65dB
- 2113 ... -64dB
- 1730 ... -63dB
- 1303 ... -62dB
- 0125 ... -61dB
- 2024 ... -60dB
- 1631 ... -59dB
- 1205 ... -58dB
- 2502 ... -57dB
- 2621 ... -56dB
- 0523 ... -55dB
- 2026 ... -54dB
- 0306 ... -53dB
- 0604 ... -52dB
- 0316 ... -51dB
- 1235 ... -50dB
- 0515 ... -49dB
- 0335 ... -48dB
- 0624 ... -47dB
- 1524 ... -46dB
- 3013 ... -45dB
- 0616 ... -44dB
- 1525 ... -43dB
- 0427 ... -42dB
- 2227 ... -41dB
- 2524 ... -40dB
- 2335 ... -39dB
- 1635 ... -38dB
- 2516 ... -37dB
- 3331 ... -36dB
- 3232 ... -35dB
- 2526 ... -34dB
- 3016 ... -33dB
- 3007 ... -32dB
- 2536 ... -31dB
- 3332 ... -30dB
- 2636 ... -29dB
- 3205 ... -28dB
- 3503 ... -27dB
- 3304 ... -26dB
- 3117 ... -25dB
- 3423 ... -24dB
- 3404 ... -23dB
- 3207 ... -22dB
- 3713 ... -21dB
- 3623 ... -20dB
- 3533 ... -19dB
- 3334 ... -18dB
- 3614 ... -17dB
- 3605 ... -16dB
- 3714 ... -15dB
- 3237 ... -14dB
- 3534 ... -13dB
- 3417 ... -12dB
- 3706 ... -11dB
- 3517 ... -10dB
- 3725 ... -9dB
- 3626 ... -8dB
- 3536 ... -7dB
- 3726 ... -6dB
- 3636 ... -5dB
- 3537 ... -4dB
- 3727 ... -3dB
- 3637 ... -2dB
- 3737 ...  0dB

**Main Menu Order**
-  1	Startup Logo
-  2	Cell Voltage
-  3	Startup Tone
-  4	Startup Text
-  5	Voice Prompt
-  6	Key Beep
-  7	TX Tone
-  8	Dual Display
-  9	TX Priority
- 10	Power Save
- 11	Freq Step
- 12	Squelch Level
- 13	Backlight
- 14	Lock Time
- 15	Time of Talk
- 16	VOX Level
- 17	VOX Delay
- 18	NOAA Monitor
- 19	FM Standby
- 20	Tail Tone
- 21	Scan >Dir<
- 22	FSK ID
- 23	Repeater Mode
- 24	Scan Resume
- 25	Scan LED
- 26	CTCSS/DCS
- 27	RX CTCSS/DCS
- 28	TX CTCSS/DCS
- 29	TX Power
- 30	Mic Gain
- 31	Modulation
- 32	Bandwidth
- 33	Scan L? >Scan
- 34    Ch -> Scan L1
- 35    Ch -> Scan L2
- 36    Ch -> Scan L3
- 37    Ch -> Scan L4
- 38    Ch -> Scan L5
- 39    Ch -> Scan L6
- 40    Ch -> Scan L7
- 41    Ch -> Scan L8
- 42	Busy Lock
- 43	Invert Speech
- 44	DCS Encrypt
- 45	Mute Code
- 46	Channel Name
- 47	Save Channel
- 48	Delete Channel
- 49	Side Key 1 LP
- 50	Side Key 1 SP
- 51	Side Key 2 LP
- 52	Side Key 2 SP
- 53	Key 0 LP
- 54	Key 1 LP
- 55	Key 2 LP
- 56	Key 3 LP
- 57	Key 4 LP
- 58	Key 5 LP
- 59	Key 6 LP
- 60	Key 7 LP
- 61	Key 8 LP
- 62	Key 9 LP
- 63	Key * LP
- 64	Key # LP
- 65	Key Menu LP
- 66	Key Exit LP
- 67	Reset Keys
- 68	DTMF Delay
- 69	DTMF Interval
- 70	DTMF Mode
- 71	DTMF Select
- 72	DTMF Display
- 73	Dark Theme
- 74	Reboot
- 75	Firmware

**Scan lists and Scanning**

There are 8 scan lists plus scan all. Active lists are displayed in the status bar when scanning.

The current channel can be added to any scanlist using the Ch -> Scan L# menus.

The scanlist to be used can be selected in the Scan L? >Scan menu.

To ignore scanlists and scan all channels, select Scan All.

To add/remove current channel to/from current scanlist, use the +/- Scan L# shortcut which is Key 9.

To start scanning, press a key mapped to the Freq scanner shortcut (default: short press side key 2).

When scanning is in progress, use side key 2 (short press) to change the scan list. This action will move to the next non-empty scanlist, or switch to scan all mode if all subsequent lists are empty.

To change the direction of current scan, use the up/down keys.

To force the scan to resume when the scanner stops on a signal, use the up/down keys.

Press any key other than Freq scanner to stop scanning.

Alternatively use Chirp Next to store scan list memory.

**Chirp Next**

Chirp Next instructions: Open in Developer mode, restart, load module (a modified Python driver), select View "Show extra fields" to display scan lists. There needs to be at least 2 frequencies per scan list but no max limit. Duplicate frequencies can be added to more than one list. Try the example .img file which contains 16 PMR446 frequencies in Scan List 1. 

2 driver files available, latest is chirp-next-radtel-rt-890-m7ocm.py Download/upload to radio use:

- Vendor: Radtel, Model: RT-890 M7OCM
- Vendor: Ruyage, Model: UV58Plus (older version)

The Chirp driver is a WIP. 8.333kHz channels can be entered and saved as can any frequency in the range 10MHz to 1.3GHz. All modulation modes. Scan Lists can be modified. Border colour can be changed and basic radio functions adjusted. Not all key actions save however. A key reset Menu #67 after upload fixes that. I advise making copies of data files on a regular basis just in case a file becomes corrupted which may happen when switching between different firmware versions (latest always works).

Note. When entering a 8.333kHz frequency in Chirp, this needs to be entered in its entirety eg 118.00833 (note the 5 decimal places). Attempting to enter or copy/paste from a CSV file something like 133.91667 or 133.91670 will not work. Enter the full correct step size ie 133.91666.

**FM Broadcast (FMB)**

Default [0/FM], toggle FMB On/FMB Idle. The 4 digit FM frequency now appears in the upper left part of the status bar. It works the same as stock just without the garbage graphics. Turn on FM Standby via menu, and you can listen to FMB while scanning/searching. When a signal is present the FM radio will mute, then continue until another signal appears - pretty cool! Note using the FMB after Spectrum may result in poor reception, no reception or work as normal, this is generally linked to specfic bands such as 440 MHz (probably many more). Open squelch to reset chip registers usually works, reboot, or select scan then FMB. This is a known issue. The radio uses a dedicated FMB chip not the BK4819. Resetting the latter clears any issues though.

To clear press [0/FM].

**Status Bar**

(l-r) Padlock = Lock, FMB, V = VOX, Scan List #, D = Dual Standby/S = Single RX, Repeater Mode "-" = No RX Subtone, "=" = Monitor Input, TX Tone A = Roger Beep A, B = Roger Beep B, I = Send FSK ID, Battery Icon = Cell charge status.

The default border color used is grey (33808). The code change can be made in Chirp or Radtel's CPS software. Please note if using the latter to change logo or border colour, CPS will throw an error after reading from radio. Nothing else gets changed during upload, but best save a Chirp back up file before proceeding. Always download to radio first, don't change border colour and upload as the data will/could get corrupted and/or overwritten (backup data regularly just in case).

**Speech Inversion Frequencies**

- 1 1350Hz
- 2 1400Hz
- 3 1450Hz
- 4 1500Hz
- 5 1550Hz
- 6 1600Hz
- 7 1650Hz
- 8 1700Hz

![20241124_154026](https://github.com/user-attachments/assets/d4bbf956-dd22-47fe-b5ad-f6369c8738e7)

## Features in latest version

- RX is unlocked 10 MHz to 1.3 GHz CAUTION experimental use only. BK4819 (useable) RX is approx 50-600 MHz; Reception outside of this range is possible but not guaranteed; radio may also exhibit erratic behaviour.
- TX 2m/70cm officially, plus various VHF/UHF bands 136-470 MHz. Output varies by band: 2-6W generally on High; max 3.6W on Low power - all figures approx - your mileage may vary 💀 CAUTION do not TX outside of chip specification, it could destroy your radio and/or breach your country of residence radio communications laws/license agreement 💀
- 0.01 kHz to 5 MHz steps
- 999 channel memory
- (N/W)FM, (N/W)AM and SSB (SB) (LSB/USB) modulation
- Light and dark theme, user selectable
- Restyled ui, fixed alignment issues, renamed menu items, new use for status bar (Scan List #), colour changes, font changes, improved clarity etc
- Squelch sensitivty and S-meter revisions
- Extended monitor functionality with up/down keys (monitor open)
- DCS RX revised/Freq Detect DCS fixed
- PTT BCLO TX during monitor revised, PTT now TX when monitor is open
- RSSI timer speed reduction to reduce internal RFI caused by SPI (screen) updates
- Full colour spectrum with control options, views
- AM Fix ported from 1 of 11's UV-K5 firmware (modified by me)
- DTMF/FSK dialog operation is now dual mode only, no FSK ID/DTMF decode dialog box in single/register screen
- RF Gain Control and Register Editor
- Flashlight Mode
- NOAA Monitor
- Custom side key and configurable "quick access" keypad keys
- Clock speed 120 MHz (stock 72 MHz)
- Display BK4819 AGC Modes/battery voltage registers in single VFO mode
- Display dBM when receiving (calculation accuracy revised)
- Reworked scan functionality
 - 8 Scan lists plus scan all
 - Scan speed is maxed out faster than stock (works in search too)
 - Resume mode: Time/TO (5.5s), Carrier/CO (2.5s), No resume/SE
 - Change scan direction while scanning (up/down keys)
 - Force scan resume (up/down keys)
- Reworked main-sub menu system, renamed items

Important note, the 10 character name tag font is UPPER CASE English alphanumeric only and limited in special characters/punctuation: . : - = < > @ ?

Please note the files herein are two colour themes (light/dark) only, not multiple colour versions that can be switched within the radio menu.

**Disclaimer, experimental firmware on a radio known for spurious signals and harmonics... what could possibly go wrong?!** 🧯

**Use at own risk, no guarantee anything will work correctly or as intended. Back up your SPI with OEFW firmware flasher tool before using (see files) and radio data with Chirp Next.**

## OEFWCOM

OEFWCOM is an ongoing development project by enthusiasts, in their own time and for no financial gain. Testers are encouraged to provide feedback to the developers, without it, progess and implementation is unlikely to happen. So please do get involved.

[Telegram RT890 OEFW](https://t.me/RT890_OEFW)

[OEFWCOM](https://github.com/OEFW-community/RT-890-custom-firmware)

## OEFW/OEFWCOM

[DualTachyon](https://github.com/dualtachyon)

[CR7BLE](https://github.com/jcalado)

LCiccio

Marcos

[Omegatee APRS HW Mod](https://github.com/omegatee/RT-890-APRS-GPS-Feat)

[Psy97x](https://github.com/Psy97x)

[Reppad](https://github.com/Reppad)

[Superogira](https://github.com/superogira)

[Tunas1337](https://github.com/tunas1337)

[Xawen](https://github.com/xawen)

Many thanks to them all!

73

M7OCM

[Supporting Open Edition Firmware](https://ko-fi.com/dualtachyon)🔚
