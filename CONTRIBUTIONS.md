# Contributions

This project needs contributions in the form of data.

The data required is CIE xyY or XYZ co-ordinates of the R, G, B primary chromaticities of any given display, as well as its white point.

# Displays to measure

Almost anything.  CRTs of course, however things like screens of different handheld devices would be useful.  For example, there's notable white point difference in various GameBoy Advance, Nintendo DS and Nintendo Switch screens.  Documenting these and building colour profiles would be interesting, and useful for emulation tools. 

More modern devices like LCD PC monitors are probably less interesting. These have a number of controls to adjust the colours on the displays, so their limits aren't as interesting.

Finding the extreme limits of old CRTs is more interesting, and likewise fixed displays like handheld consoles are too. 

# Equipment and software

You will need:

* An electrically calibrated display. For things like CRTs, all internal voltages should meet the manufacturer's service manual specifications.
* A display with relatively low power-on hours. This is getting more difficult as time goes on. If you know the runtime hours of the device, let me know. 
* A decent quality colorimeter.  The "Calibrite Colorchecker Display" family of colorimeters are decent quality for the asking price.
* For SD SDR displays, attempt to get peak brightness in the range of 80-100 nits. Be careful not to grossly under or over drive the display. Check both the manufacturers specs and the colourspace spec you are working with.  Because we're looking for the extreme points of the gamut, we're not so worried about black levels, only 100% white and saturation points.
* The white point should be calibrated to the spec/setting of the device.  i.e.: if it's been set to 6500K in the system menu, ensure that is in fact the white point.  Likewise if you've chosen 9300K. 
* Software to generate colour patterns.  Ideally you want a 10% window to avoid over-driving displays with 100% brightness images.  The images themselves need to be 100% Red, Green, Blue and White.  You can use software like:
  * 240p test suite - https://junkerhq.net/xrgb/index.php?title=240p_test_suite
  * AVS HD 709 discs - https://www.avsforum.com/threads/avs-hd-709-blu-ray-mp4-calibration.948496/
  * My own FreeCalRec601 DVDs - https://github.com/danmons/FreeCalRec601
* Software to measure the output, such as
  * HCFR - https://sourceforge.net/projects/hcfr/
  * Argyll CMS -  https://www.argyllcms.com/

If you have your own tools/methods for capturing this data, that's fine.

If not, you can use "Argyll-CMS" - a free command line tool.  It comes with "spotread", which will do a one-time read of a display and produce results in absolute CIE XYZ and CIE Lab output. 

# Capture process

As above, you can use any tool you like to capture this data.  An example capture process using Argyll-CMS is:

* Let your display warm up for 15 minutes or so.  You can use it during this time for content playback or gaming, just don't take measurements until it's been on for a while. 
* Generate a picture with a tool that can show 100% R, G, B and white images. Some options mentioned above. 
* Ideally you want a 10% window (or just larger than your colorimeter's lens if 10% is too small) to stop colour distortion happening when full screen pure signals over-drive the tube. 
* Attach the colorimeter, bring up a 10% window of 100% pure white, run:
 ```
 spotread -c1 -yr -ew
 ```
* Spotread will take an absolute white reference measurement. 
* Once done, change to a 10% window of 100% red, press enter and take a measurement
* Repeat for green and blue. 
* Press Q to quit, save the data to a text file. 

Ideally, repeat the entire process from scratch so that the initial absolute white point read is re-taken. 2-3 repeats will help with narrowing down errors. 

You should see data similar to this sort of output (this is a full NES colour palette read, so it's longer. Yours will just be 4 lines - the white reference plus R, G and B)
* https://stickfreaks.com/colour_nes_rawdata/2020-11-22_rawdata/avfamicom.txt

Create an issue here in this repo, and supply your data.  Ensure you mention how you'd like to be credited for the contribution. 
