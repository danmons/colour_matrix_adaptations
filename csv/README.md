# CSV content

The files `matrix_XYZ.csv`, `matrix_sRGB.csv`, `matrix_BT709.csv` and `matrix_BT2020.csv` are output by the Jupyter notebook "chromaticity_matrix_calculations.ipynb".  Run it to regenerate the file, and/or add in more chromaticity co-ordinates to generate further output.  (Also, feel free to contact me if you discover more useful co-ordinates you'd like to see added to this public repo).

This is a plain-text, comma-delimited CSV file encoded in simple ASCII/UTF-8. 

The file contains the following headers, left to right:

## col_id

A unique identifier that can be used programmatically. 

## col_desc

A human-readable colourspace description.  Reference only, unused mathematically. 

## eotf

A human-readable EOTF (Electro-Optical Transfer Function), aka "gamma".  Reference only, unused mathematically. 

## Wx, Wy

The (x,y) co-ordinates in CIE xyY colourspace of the whitepoint. For CIE standard illuminant D series, these should be calculated via the 2018 adjusted Planck Constant c2. However if these belong to a given standard spec (CCIR / ITU-R / EBU / SMPTE / etc) and differ slightly from perfect calculations, I'll use the values from the spec.

## Rx, Ry, Gx, Gy, Bx, By

The (x,y) co-ordinates in CIE xyY colourspace of the R, G, and B primary chromaticities. For specification based systems these are taken from the matching specifications.  For measured based systems they are taken from supplied measurements, typically with a decent quality colorimeter on a device that has been professionally serviced and electrically calibrated to match voltages and outputs as recommended by the manufacturer's service manual. Individuals who supply these values will be credited in the description fields. 

## Msrc0, Msrc1, Msrc2, Msrc3, Msrc4, Msrc5, Msrc6, Msrc7, Msrc8

These are specific to the `matrix_XYZ.csv` only. These 9 values represent the 3x3 "Source Matrix".  You should only use the Source Matrix on the source image, and use it for the colourspace/display you wish to simulate.  i.e.: if you want to simulate, say, a Japanese Super Famicom displayed on a Japanese Sony PVM, you could use one of the measured PVM Source Matrices and/or ARIB TB B9 v1 matrix with a D93 white point. 

## Mdst0, Mdst1, Mdst2, Mdst3, Mdst4, Mdst5, Mdst6, Mdst7, Mdst8

These are specific to `matrix_XYZ.csv` only. These 9 values represent the 3x3 "Destination Matrix".  You should use the Destination Matrix that matches the physical display being used to show the image.  So for example, for a user on a standard PC LCD monitor, you would most likely use sRGB D65.  For users on a modern HD TV, BT.709 D65.  For a user on a modern UHD (sometimes incorrectly called "4K") TV with standard-accurate wide colour gamut, you could use BT.2020 D65. 

It is somewhat unintuitive, as the temptation would be to use the matrix describing the source as a "filter" on destination, however this is the wrong way around.  The Source Matrix must describe how the original source was intended to be displayed, and the Destination Matrix must describe the modern screen you are displaying that source on. 

## M0, M1, M2, M3, M4, M5, M6, M7, M8

These are combined input/output matrices in `matrix_sRGB.csv`, `matrix_BT709.csv` and `matrix_BT2020.csv`.  The skip the intermediate conversion to XYZ colour space, saving a calculation on lower powered devices.  The sacrificing being that you can the no longer utilise that middle step to do further colour modification, however if you have a lower power device, you may not want to anyway. 

See FAQ_USAGE.md in the main repo for the correct sequence of steps on how to apply these matrices correctly and achieve the most accurate output. 
