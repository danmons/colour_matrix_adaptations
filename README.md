# Colour Matrix Adaptations

This repo contains a number of matrices you can use to convert anything in any given arbitrary colour space, colour standard or specific monitor/CRT/display characteristics to any other. 

The end goal is for these to be useful to developers of things like: 
* Shaders used in emulation software
* Filter effects used on video playback systems
* Colour correction used in output scalers of FPGA systems
* Hardware mods in retro game consoles that produce high resolution digital output
* Hardware scaling devices that convert low resolution analogue or digital signals to high resolution ones

Almost all of the work in this repo is based on the maths provided by Bruce Lindbloom here:
* http://www.brucelindbloom.com/Eqn_RGB_XYZ_Matrix.html

The matrices are in the `csv` folder, as `matrix_XYZ.csv`, `matrix_sRGB.csv`, `matrix_BT709.csv` and `matrix_BT2020.csv`, .  A README.md document in there documents the data format.  

Also in this repo are a number of Jupyter notebooks (interactive Python web forms) that demonstrate the maths in action, including verifying against Bruce Lindbloom's pre-baked matrices, as well as testing on images to produce visual output to compare against real world displays. These are not required for people who simply want to use the matrices in question, but are provided for others to check/verify/reproduce the work, and/or learn how the sausage is made. 

# What's the point? 

How an image looks on a screen is dependent on many things.  The biggest influences on the colour especially come down to two main features. Firstly, the regional standards that display used, such as various US/NTSC vs EU/PAL vs Japanese standards. The often-debated feature here is whether or not the authors of the content intended to use western-standard D65 white points, or 1990s-Japanese-standard D93.  For more on what this means, see the "FAQ_D93.md" file.

The second major feature is the physical characteristics of the display.  While we are quite used to modern standards like ITU-R BT.709 that define exactly how a HD screen should look and behave, in the 20th century the variance of displays came down to even the fact that certain brand CRTs had different phosphor compounds on their screens, so that the primary Red, Green and Blue colours looked subtly different to the human eye.  While ideal standards existed for colour spaces, physical differences in displays of the era, and the lack of strict adherence to these meant that the final visual output would be different. 

These matrices can be used to simulate any colour system imaginable on a modern display.  The advantages on offer are that users can simulate the given display characteristics of devices that may be too expensive/rare/difficult to acquire, and that the user could (given the tooling of the given scaler/emulator/whatever) in theory be able to switch these colourspaces in realtime without needing to re-calibrate their entire display to some other colourspace (and back again when they were finished).  As long as their display is close to the given standard common output system (which many modern displays are these days when set to "expert" presets), they can be reasonably confident the output is fairly consistent with the simulation intended. 

# Caveats

Because some current-yet-limited standards like sRGB (still the most prevalent standard in PC monitor displays) and BT.709 (likewise, the most prevalent standard in HD displays) are limited in the colour gamuts, the output from these matrix conversions will clip certain extreme colours (anything on the very edge of the colour gamuts, such as 100% saturated colours, or 100% white). This isn't necessarily a huge sacrifice, however. Most systems don't use 100% saturation of colours for the bulk of content (even old games which tend to use bold colour palettes). And where the clipping does occur, the actual colour corrections are often still good enough to show a close approximation up to the clipping point. 

For purists, the best result always will be attained by using the widest colour gamut display possible.  From a consumer standpoint in 2023 when this document is being written, that means using a display that can handle standards such as BT.2020 (the standard domestic UHD colourspace, sometimes incorrectly called "4K" or "HDR"), or the slightly less commonly used Display-P3 (used in certain phones and Apple displays, not to be confused with DCI-P3 which is a slightly different cinema/theatre standard rarely used outside of professional commercial cinemas, and content that consumers cannot get their hands on).  Both of these can cover the full gamuts and colour volumes necessary for the conversions without clipping.  These systems have added advantages when paired with HDR to be able to produce higher luminance images (good for compensating for BFI, scanlines, shadow masks, etc) or to simulate specific strange gamma curves.  However these advanced luminance/gamma options are out of scope for this project, as it purely concentrates on R/G/B primary and white point chromaticities only (i.e.: the defining characteristics of a gamut / colour volume, and independent of luminance). 

# How do I use these matrices? 

See FAQ_USAGE.txt for a block diagram and walkthrough. 

# Which matrices should I use? 

This is largely down to personal preference, however I've put together a "FAQ_RECOMMENDATIONS.md" you can read that have my own personal recommendations in there, dependent on what source material you are using, or what device you wish to simulate.  Again, I stress these are purely subjective, and there's no right or wrong way to view the content.  
