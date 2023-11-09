# MiSTer FPGA D93 simulator

The MiSTer FPGA gamma scaler only applies to the greyscale.  As such, individual R,G,B chromaticities have no effect, only the white point matters. 

These files are produced by the `mister_fpga_gamma.ipynb` notebook.  

As D93 is out-of-gamut for D65 colourspaces, two scaled versions are offered as well as the standard one to reduce severe clipping, but this comes at the expense of brightness. For a visual explanation of this, see the notebook [compare_gamut.ipynb](../jupyter/compare_gamut.ipynb) in the jupyter folder.

Put these files in your `/media/fat/gamma` folder on your MiSTer FPGA device, and select them from the Video Processing -> Gamma Correction menu. 

