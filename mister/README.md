# MiSTer FPGA D93 simulator

Generated outputs for MiSTer FPGA.  These are transferred to the following repo for use with MiSTer's `update_all.sh` script:
* https://github.com/danmons/MiSTer_D93

Instructions on how to use them are in the repo above. 

The MiSTer FPGA gamma scaler only applies to gamma curves.  As such, individual R,G,B chromaticity co-ordinates are not changed, only the white point is affected.

i.e.: This won't do full unique CRT simulation like some of the other tools and matrices in this repository.  It will only simulate a D93 white point. 

These files are produced by the [mister_fpga_gamma.ipynb](../jupyter/mister_fpga_gamma.ipynb) notebook.  

As D93 is out-of-gamut for D65 colourspaces, two scaled versions are offered as well as the standard one to reduce severe clipping, but this comes at the expense of brightness. For a visual explanation of this, see the notebook [compare_gamut.ipynb](../jupyter/compare_gamut.ipynb) in the jupyter folder.
