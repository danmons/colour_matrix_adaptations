# D93 FAQ

## Just give me the short version, Dan.  

Japanese content created for colour displays in the late 20th century often targets a cooler "D93" (9305K) white point compared to the "D65" (6504K) white point used in displays in the west at the time, and displays almost exclusively used now in the 21st century. If you're reading this on a modern computer, tablet or phone, chances are you're looking at a D65 display. 

Watching content from this era on modern displays means the colours look "wrong", as they assume your display os configured differently.  However with modern technology we can apply non-destructive colour correction at time of display to adjust these colours to how they were intended to look, without needing to adjust our displays constantly.

Enthusiast users may go as far as to buy, calibrate and use era-matching display technology like CRTs, and calibrate these to the standards documented here. However in the modern world of modern computers and wide gamut TVs and monitors, we can now very accurately convert and display these images in realtime without needing to adjust our TV settings constantly. We could even go as far as simulating several makes and models of CRT output for user selection, similar to things like the shadow mask filters and shaders many emulators and hardware image scalers do today. 

Doing so requires some documentation of these standards, and then maths to convert the data correctly.  This repo will attempt to document both. 

## I need to see pictures, Dan. 

Sure. Here you go:
* https://www.retrorgb.com/colour-malarkey.html

## What is the term D93? 

D93 is a term used to describe the colour temperature of a white point. The term derives from the temperature a "black body" (a hypothetical perfect object in space) would be if it was approximately the temperature 9300K (9027 degC, 16280 degF). The "D" refers to the standard illuminant D series, defined by the CIE. 

Visible white light from the sun is a mix of light across the entire visible colour spectrum. This then changes as it moves through our atmosphere and enters our eyes. The Earth's sun has a surface colour temperature of 5772K, however depending on your latitude (north/south position) on the planet, as well as the time of day, this white light will change appearance. It can look bluer, or what we call "cooler" during the day. This can be a little confusing, as in physics, a hotter black body producers bluer light, which we call "cooler" (associating the colour blue with something cool). Conversely cooler black bodies produce redder light, which we call "warmer" (associating the colour red with something warm). So as such, a colour temperature like 9300K will look "cooler" than 6500K, as by comparison 9300K is "bluer" than 6500K. 

As colour display technologies matured in the 20th century, there was a drive to standardise how colour is defined. Various standards groups were formed, and the blue sky of mid-latitude northern Europe (similar to North America) was used as the basis to define white light in broadcast television.  This was deemed to be D65 (approximately 6500K, later adjusted slightly), and is part of the Standard Illuminant D Series of white points (D50, D55, D65 and D75). As such, most consumer display technology in the west standardises this white point.  It's the white point for common TV standards like ITU-R BT.601 (SD Television), BT.709 (HD Television), BT.2020 and BT.2100 (UHD Television in both SDR and HDR), sRGB (PC displays), AppleRGB (early Macintosh systems), and many others. If you are reading this now on a computer, tablet or phone, you are probably looking at a device with a D65 white point. 

However in Japan, the comparatively cooler "D93" was deemed to be the preferred white point during the late 20th century. There's still quite a lot of debate around if "D93" is even a formal standard or not, as it's often left out of the list of standard illuminants. However there exist several standards documents from various groups that reference the white point both by "D93" notation, and by colour temperature.

## What is a colour standard? 

Various display standards exist to define colour, typically driven by the physical limitations of technology at the time.  The CIE 1931 x y Chromaticity Diagram is typically used, as it shows all colour visible to human beings. Human vision is broken into three types of colour receptors in the eye (called "cones"), sensitive to long (red), medium (green) and short (blue) wavelengths, and light volume (called "cones"), which are sensitive to the volume of photons. As such, most colour displays use red, green and blue "primary" wavelengths to mix and simulate other colours for humans to see. 

We define various colour standards for displays using the following data:

* The white point co-ordinates 
* The RGB primaries co-ordinates
* The minimum and maximum brightness
* The EOTF (Electro-Optical Transfer Function), sometimes called "gamma"

The RGB primaries form a triangle on the diagram which we refer to as the "gamut".  However the entire colour volume is 3D shape, and different colour standards can produce specific colours that some other standards cannot show.  This is obvious for a "wide gamut" standard like BT.2020 compared to BT.709 where BT.2020 has many colours outside of the BT.709 gamut. Likewise HDR standards like BT.2100 can produce both brighter and darker levels than SDR standards like BT.709.  In those cases, converting from a smaller range to a higher range is fine, however going from a higher range to a smaller range requires either clipping or scaling (sometimes called "tone mapping") either the colour or brightness data that is out of gamut, or out of range. 

Many of these standards relate directly back to CRTs. A CRT (Cathode Ray Tube) works by firing an electron bean charged by an anode, which then moves towards the cathode screen (manipulated by fast moving magnetic fields). The cathode screen is coated in phosphors which then light up temporarily as the beam strikes them in a single point. The specific type of phosphors used give off specific wavelengths of light, and these phosphors traditionally defined the RGB co-ordinates of given standards. The brightness of the display across the greyscale in CRTs tends to follow a curve rather than a straight line, hence the need for gamma curves to produce images with correct brightness/contrast levels. 

Phosphors used in CRTs in Japan in the late 20th century sometimes differed from those used in the rest of the world, and as such the RGB co-ordinates for common standards of that era like BT.601 and sRGB don't quite align with the actual wavelengths produced by the phosphors.  These differences are minor, however documenting them allows us to adjust display output to simulate a given made and model of CRT in realtime on a wide gamut standard like the now standard BT.2020 on most UHD "4K" TVs. 

# Why 9305K and not 9300K?

Initially when these standards were defined, there were slight errors in Planck's Constant, which is used in black body radiation maths.  Since then, the constant has been adjusted to be more accurate, and so the numbers and maths used also must adjust. 

The old value for D65 was 6500K, and for D93 was 9300K.  Multiplying these numbers by a ratio of 1.438776877/1.4380 gives:
* D65 = 6503.512 , rounded to 6504
* D93 = 9305.024 , rounded to 9305

For calculations in this repo, higher accuracy values will be used. For simplicity, the terms "D65" and "D93" will be used. 

## What are the colour standards for D93? 

This repo will attempt to document these.  These can be collected from data we can find (standards groups like Japan's ARIB - Association of Radio Industries and Business) or in technical documements from companies like Sony.  Also measurements of actual devices (particularly CRTs) can be used to discover the chromaticity values of the primary colours.

Contributions of measured chromaticity co-ordinates are welcome, and will be attributed to the people collecting the data. 

## What's in this repo?

The `d93` folder contains collected documents from around the Internet that mention anything to do with D93, Japanese CRT phosphors, RGB chromaticity co-ordinates, etc.  Included will be the URL or ISBN they were sourced from, a "pdftotext" conversion for easy text searching, and machine translated versions if not in English. 

The `jupyter` folder contains Jupyter notebooks.  These notebooks are working spaces to play with code and maths in the Python programming language, and are designed to be verbose enough that they explain the maths in a "pseudo-code" style manner for anyone wanting to implement these functions in other languages (say, port them to various shader or FPGA languages).  Notebooks can be viewed read-only on GitHub, or can be downloaded and used interactively either in Jupyter directly (install Python on your computer, and common Python libraries like jupyter, numpy, Pillow, etc, and then run "juptyer-notebook" to interact with these in a browser).  Some editors/IDEs like VS Code (and the open source vscodium) will also run interactive Jupyter notebooks.
