# How to use the matrix data

It's quite critical to follow these steps in order.  Following these out-of-order will produce inaccurate output (often quite visually obvious). 

The steps to use the matrices are

1) Acquire an input.  This can be in the form of a framebuffer inside an emulator, a frame captured by a capture device, a generated output from an FPGA system, etc. If the input frame is in the some non-RGB colourspace (YIQ, YUV, YPbPr, etc), it should be converted to RGB.

2) Normalise the RGB data from whatever bitrate it was captured/created as down to 0.0-1.0.  When doing so, be careful to include compensation for limited/narrow/full RGB ranges. 0.0 should represent 0%, or the darkest / least saturated value for that channel, and 1.0 should represent 100% or the brightest / most saturated value for that channel. 

3) Once normalised to 0.0-1.0, remove the EOTF (Electo-Optical Transfer Function), commonly referred to as the "gamma".  Not that specific specs have specific gammas.  sRGB, for example, has a non-linear gamma with a flat portion at very low values.  Other systems may have a much simpler power law.  There can also be subtle (or even extreme) differences in display specification gammas versus what some retro consoles actually spit out.  As such, the gamma removal here is up to the developer to choose.  However you should end up with linear RGB values.

4) Once the value is a normalised and gamma/EOTF removed, apply the SOURCE MATRIX.  It's quite critical here to understand the order of which matrix is applied when.  The source matrix conversion will assume the white point and RGB chromaticities of the source.  So for example, say you were capturing a Japanese Super Famicom and region-matching game, or wanted to simulate a Japanese Sony PVM, you could choose a SOURCE MATRIX such as the ARIB TR B9 v1.0 or measured Sony PVM devices, and choose D93 as the source whitepoint.  Again, critical to do this at the SOURCE side, and this should measure the colourspace you wish to simulate and/or colourspace where you assumed the content came from. 

This step then converts that RGB value to XYZ colourspace. XYZ is absolute, always-positive, linear, and completely independent of white point representations (hence why we need the SOURCE MATRIX to include whitepoint information for the conversion process).  This colourspace is designed for mathematical ease-of-use rather than display, and once in this colourspace, it is easy to do further manipulations to the colour if desired.  Here is a good place to do things like linear brightness controls (in XYZ, the Y value is luminance, and can intuitively be controlled so that a +10% change results in a +10% brightness/luma change without affecting colour/chroma). Similarly, doing manipulations like further shaders, shadow masks or whatever can be done at this step if desired. 

5) Now apply the DESTINATION MATRIX.  This should match the physical display the user is on, including the white point of that display.  Don't get confused here and assume you need to choose something like D93 white point - that should be chosen on the SOURCE instead, as it made those conversions/adaptations at that time.  The DESTINATION MATRIX should always match the physical device the end-user is looking at, including the white point of that standard. Typically these will be one of:
* sRGB D65 for users on standard PC desktops
* BT.709 D65 for users on HD TVs
* BT.2020 D65 for users on UHD (sometimes incorrectly called "4K") TVs with matching wide colour gamut. 

6) You now have normalised 0.0-1.0 RGB values in the colourspace desired.  Next apply the EOTF/gamma of your display device, which is typically:
* sRGB's non-linear gamma, near 2.2 with exception for near-black levels (the exact formula can be found on wikipedia)
* BT.709 displays use BT.1886.  This is optionally either a standard 2.4 power law, or the spec provides a secondary mode for simulating CRT characteristics, which can be pleasing where the content was originally coming from CRT
* BT.2020 can either use BT.1886 in SDR mode, or PQ in HDR mode. Other EOTFs like HLG exist, although PQ is by far the most common.

7) You now have normalised 0.0-1.0 RGB with gamma/EOTF applied.  From here, scale up to whatever bit depth is required (typically 8bit for sRGB and BT.709, 10 or 12 bit for BT.2020), and if needed convert to limited/narrow range RGB or any other output colourspace and chroma subsampling required for final display. 

Within the "jupyter" folder is a series of reference images.  Various matrices have been applied to these, and the resulting output is in teh "out" folder.  These can be used as visual references to see what expected SOURCE -> DESTINATION conversions should look like.