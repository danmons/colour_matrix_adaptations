# Matrix Recommendations

This document lists the author's recommendations for which matrix to use depending on source / destination items. 

Note that these are recommendations ONLY.  If you want to do something custom, feel free.  If you think I'm wrong, find me on the socials and have a chat. I'm very willing to change my mind if there's enough documentation about, or new measurements show up. 

General consensus is: "Japan SD/ED era = D93, Everything else D65" and pick matrix specs roughly in line with that era, territory and technology. 

But also, you know... https://xkcd.com/927/

This is all very pedantic, and many of these settings will only have very slight impacts on final images. If you're a technology history buff, you'll probably care a lot.  If you just want to play/watch old things, you might not care so much.

## Source Matrix

* Simulate Japanese PVM
  * Source Matrix: Raney Sony PVM-20M2U
  * Source White Point: D93
  * Source EOTF: gamma 2.25

* Japanese Hi-Vision / MUSE
  * Japanese VHS, DVD
  * Source Matrix: NTSC-J ARIB
  * Source White Point: NTSC-J ARIB spec (near D93)
  * Source EOTF: BT.601 spec (non-linear, near gamma 2.2)

* Japanese authored TV-console games, SD (Standard Definition - 240p/480i modes)
  * MSX
  * Nintendo 8bit, 16bit, N64, GameCube, Wii
  * Sega 8bit, 16bit, Saturn, Dreamcast (not VGA out)
  * Sony PlayStation 1, 2
  * Microsoft Xbox
  * Source Matrix: NTSC-J ARIB
  * Source White Point: NTSC-J ARIB spec (near D93)
  * Source EOTF: BT.601 spec (non-linear, near gamma 2.2)

* Japanese authored TV-console games, ED (Standard Definition - 480p modes) 
  * Nintendo GameCube, Wii
  * Sony PlayStation 2
  * Microsoft Xbox
  * Source Matrix: NTSC-J ARIB
  * Source White Point: NTSC-J ARIB spec (near D93)  
  * Source EOTF: BT.1886 spec (non-linear, near gamma 2.4)

* Japanese authored PC/VGA games (640x480/800x600/1024x768/1280x1024/etc)
  * IBM PC, PC-88, PC-98, Sharp X68000
  * Sega Dreamcast in VGA out mode
  * Source Matrix: sRGB
  * Source White Point: D93
  * Source EOTF: sRGB spec (non-linear, near 2.2)

* Japanese authored console games, HD (High Definition - 720p/1080i/1080p modes)
  * Microsoft Xbox, Xbox 360, Xbox One, Xbox Series
  * Sony PlayStation 2, 3, 4, 5
  * Source Matrix: NTSC-J ARIB for analogue systems, BT.709 for digital/HDMI systems
  * Source White Point: NTSC-J ARIB spec (near D93) for analogue systems, BT.709 spec (near D65) for digital/HDMI systems
  * Source EOTF: BT.1886 (non-linear, near gamma 2.4)

* Very old North American stuff
  * 80s VHS / Betamax / LaserDisc
  * Atari VCS / 2600 / 5200 / 7800
  * Simulate very old North American CRT TVs
  * Source Matrix: SMPTE C
  * Source White Point: SMPTE C spec (near D65)
  * Source EOTF: gamma 2.2

* North American authored console games, SD (Standard Definition, 240p/480i modes)
  * Nintendo 8bit, 16bit
  * Sega 8bit, 16bit, Saturn, Dreamcast (not VGA out)
  * Sony PlayStation 1, 2
  * Microsoft Xbox
  * Source Matrix: BT.601-525
  * Source White Point: BT.601 spec (near D65)
  * Source EOTF: BT.601 spec (non-linear, near 2.2)

* European and Australian authored console games, SD (Standard Definition, 288p/576i modes)
  * ZX Spectrum
  * Amstrad GX4000
  * MSX
  * Nintendo 8bit, 16bit, N64, GameCube, Wii
  * Sega 8bit, 16bit, Saturn, Dreamcast (not VGA out)
  * Sony PlayStation 1, 2
  * Microsoft Xbox
  * Source Matrix: BT.601-625
  * Source White Point: BT.601 spec (near D65)
  * Source EOTF: BT.601 spec (non-linear, near 2.2)

* 1970s / 1980s SECAM Television
  * Source Matrix: BT.470-6
  * Source White Point: CIE Illuminant C
  * Source EOTF: gamma 2.8

* 1990s SECAM Television
  * Source Matrix: BT.601-625
  * Source White Point: BT.601 spec (near D65)
  * Source EOTF: gamma 2.8

* Old Apple stuff  
  * Apple Macintosh family, pre-iMac
  * Source Matrix: AppleRGB
  * Source White Point: D65
  * Source EOTF: gamma 1.8 

* Non-Japanese authored PC/VGA games (640x480/800x600/1024x768/1280x1024/etc)
  * IBM PC and PC compatible clones, Apple iMac / Power Mac / Mac Pro
  * Sega Dreamcast in VGA out mode
  * Source Matrix: sRGB
  * Source White Point: D65
  * Source EOTF: sRGB spec (non-linear, near 2.2)

* Non-Japanese authored TV-console games, ED (Enhanced Definition - 480p/576p modes)
  * Nintendo GameCube, Wii
  * Sony PlayStation 2
  * Microsoft Xbox
  * Notes: Strange time, no common standard. BT.601/BT.709 variable depending on individual game. 
  * Source Matrix: BT.601-525 for NTSC, BT.601-625 for PAL. Optionally BT.709 for any. 
  * Source White Point: BT.601/BT.709 spec (near D65).
  * Source EOTF: BT.601 spec (non-linear, near gamma 2.2). Optionally BT.1886 (non-linear, near gamma 2.4)

* Non-Japanese authored console games, HD (High Definition - 720p/1080i/1080p modes)
  * Microsoft Xbox, Xbox 360, Xbox One, Xbox Series
  * Sony PlayStation 2, 3, 4, 5
  * Source Matrix: BT.709
  * Source White Point: BT.709 spec (near D65)
  * Source EOTF: BT.1886 (non-linear, near gamma 2.4)

* Brazilian authored console games, SD (Standard Definition)
  * Nintendo 8bit, 16bit, Gamecube, Wii (480i mode)
  * Sega 8bit, 16bit
  * Source Matrix: PAL-M/BT.470-6
  * Source White Point: CIE Illuminant C
  * Source EOTF: Gamma 2.8

## Destination Matrix (values recommended for highest compatibility with current market devices)

* VGA/SVGA PC CRT, LCD/OLED PC Monitor, SDR
  * Destination Matrix: sRGB
  * Destination White Point: sRGB spec (near D65)
  * Destination EOTF: sRGB spec (non-linear, near 2.2)
  * Full range RGB, 8bit

* LCD/OLED/Plasma Television, HD, SDR
  * Destination Matrix: BT.709
  * Destination White Point: BT.709 spec (near D65)
  * Destination EOTF: BT.1886 (choose first mode if HD source, choose second "CRT approximation mode" if SD source).
  * Limited range RGB, 8bit

* LCD/OLED Television, UHD ("4K"), SDR
  * Destination Matrix: BT.709
  * Destination White Point: BT.709 spec (near D65)
  * Destination EOTF: BT.1886 (choose first mode if HD source, choose second "CRT approximation mode" if SD source).
  * Limited / Narrow range RGB, 8 / 10bit

* LCD/OLED Television, UHD ("4K"), HDR
  * Destination Matrix: BT.2020
  * Destination White Point: BT.2020 spec (near D65)
  * Destination EOTF: SMPTE ST 2084 / PQ
  * Narrow range RGB, 10bit
