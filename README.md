# AstroJargon Mask Generator (Version 0.4)

This is a rewrite/conversion of the Bahtinov mask generator from the (currently) defunct website astrojargon.net.  

A Bahtinov mask is a focusing aid for astronomers (in general) and astrophotographers (in particular).  It consists of a disk made of (usually) opaque material fitted over the telescope objective with slots cut out in a specific pattern devised by amateur astrophotographer Pavel Bahtinov. For more information, look at [this thread on CloudyNights](http://www.cloudynights.com/ubbthreads/showflat.php/Cat/0/Number/2544487/page/0/view/collapsed/sb/5/o/all/fpart/1/vc/1) or here at [Spike-a.com](http://www.spike-a.com/).

Designing a mask using drawing, design, or CAD software can be challenging, as the specifics of the mask change for each telescope based on aperture, focal length, and how you plan to attach the mask to the scope. This generator makes producing masks significantly easier - simply enter values specific to your telescope, and it generates SVG and displays an image with your design.  

## Installation

There is no installer for the generator.  Unzip the file named AstroJargonMaskGenerator.zip to a folder/location of your choosing, then run AstroJargonMG.exe.  Scan it first, of course.

If you want to verify the zip file (and downloaded this readme directly from github), here's the SHA-256 hash: 

```
9128FE153DE383F1C6E8F4CBA1B443AF798D7C866A80D7C8220B33EE322197A5
```

## Environment

Windows.  Tested on Windows 10 and a Windows 7 VM.   .Net version 4.6 is required.

## What's New/Fixed in Version 0.4

- Slots on all Bahtinov variations (what what?) can now be rounded. 
- New Mask Types:
  - Couder Mask - some mystical ATM thing for testing mirrors.  *Probably* involves incense and candles.  Words like Foucault, Couder, knife edge, pitch lap, Everest stick pins, shadow zones - it all sounds pretty dark. I bet those guys are just making stuff up.
  - TriBahtinov - original design by [C.Y. Tan](https://github.com/cytan299), modified by [Satoru Takagi](https://github.com/satakagi).  A triple Bahtinov mask for collimation as well as focus.  Another long thread on [Cloudy Nights](https://www.cloudynights.com/topic/536410-a-tri-bahtinov-mask-for-sct-collimation-and-focusing/).
  - TriBahtinovIS - Satoru Takagi calls this the "2nd modified Tri-Bahtinov" mask, but I think TriBahtinovIS (Increased Sensitivity) sounds cooler.
  - TriBahtinovISMask - a mask *for* a mask - how cool is that?  Masks off portions of the TriBahtinovIS so that only one "set" of Bahtinov slots is exposed.  Original idea by [Jordi Blasco](https://github.com/jordiblasco)
- Mounting slots location was off - now centered on theta (was aligning the ride side to theta).

## What's Still Broken

- User reported a scaling issue in Fusion 360.  Would love to tackle this, but I'm having issues getting Fusion 360 to run.
- There's not a lot of input validation
- Most likely more stuff - send me an e-mail or DM me on CloudyNights

## What's Ahead**

- Different color(s) for printing text, so one color can be specified for printing and another for cutting.
- Adding override for width of ring around knockout for central obstruction (currently defaults to the "structural element width").
- Allowing specification of slot:bar ratio, with override for bar width (currently slots and bars are the same width).  Slots are the open spaces light passes through, bars are the solid bits.
- Database of telescope data (aperture/focal length/central obstruction)
- More mask types? Pitch Lap Mat - I thought astrophotographers were nuts, but ATMers take the prize.
- Help screen/better documentation - particularly License and attribution info
- Integration with Maskulator (or possibly something else, if anyone knows a more modern variant)
- Granular SVG - right now everything is flattened into a path, might be useful to have more granular control over individual shapes.
- Open Source 

​		** Not a commitment or guarantee that any of this will happen, just stuff I've thought about.

## License

No warranty, express or implied, yada, yada, yada....

## Contact

Preferred: Cloudy Nights DM - username FarmerDave 

email: polivka@gmail.com

## Version/Change History

### 0.3.0.0 01/22/2021

##### Zip File SHA: 6C38F25570E8F47AFB535D69543B12E968A2EE436D84C0F102AE33D266BE3CD8

- **MAJOR**: The mask generator threw exceptions and generated blank masks on machines where the decimal separator (radix) was specified in Window's region settings as a comma.  I apologize to the large swaths of the world I may have offended, but I actually blame Microsoft (or the authors of one of their libraries) for this one.  Huge thanks to the French, Austrian, and German users who reached out to me to let me know there was an issue. Personally, I think we should all use the interpunct.  
- Moved dowload location to github, where I eventually will host the source code (still want to clean some things up first).
- .NET Version 4.6 is required (was 4.52)
- The default mask is back to Bahtinov instead of Plain (whoops!).
- Hartmann mask - non-circular holes (microlenses, technically, I think)  and rotation, so now the Wodaski variation with three misaligned triangles is possible.  You can even use text!
- Since I added text to the Hartmann mask, I thought "Hey, maybe we could add text to the margins, or even in the overhang or central obstruction!"  You can now do that.  Note that I didn't say it was a good idea, or that it's terribly practical: if you don't use a "stencil" font, all the inner bits of your letters/digits are going to fall out.  Mildly useful if you're testing variations.
- Global options window added 
- Global options includes "rendering tolerance."  Increasing this value will speed up rendering, but decrease quality of rendering.  0.000001 is as good (slow) as it gets.  If you thought the app was slow, it's because I had this hard-coded to the minimum value.  The default is now set to 0.001, which looks pretty good and renders pretty fast.  Masks will be automatically re-rendered at the minimum tolerance before saving (unless you turn *that* option off).  Also added an animated gif to help you while away the seconds while rendering.  Note that existing users probably need to set this to 0.001 manually.
- New mask types:
  - Duncan Mask - from http://stargazerslounge.com/index.php?app=core&module=attach&section=attach&attach_id=65090, referenced in this CloudyNights thread: https://www.cloudynights.com/topic/383975-why-no-commercial-source-for-duncan-mask/ - Duncan Evenden who sketched out the original from "something he saw on the web" chimes in on page 3.
  - Perpendicular Mask - yeah, I'd never heard of it either.  From Gábor Tóth's site: http://astro.i-net.hu/node/56.  Never realized how hard spelling perpendicular was.

### 0.2.0.0 12/14/2020 

##### Zip File SHA: 5221AF99C70DABA161AC976878E565418D045DA016CEF82ACC6466EB56040D78

- Now saving input parameters as metadata in the SVG - which means you can now re-open the SVG file for a mask you designed and tweak the settings without having to re-enter everything. 
- Fixed some really janky arcs - I messed up a smoothing factor, and ended up with janky circles/arcs. Janky, janky, janky.
- Mounting options - holes, slots, or holes and slots - go nuts.
- Hartmann masks can now do multiple orbits/courses of holes, so you can (in theory) replicate the [original Hartmann mask](https://www.cloudynights.com/topic/610955-the-original-hartmann-mask/).
- Can set a color for the bounding box of the mask
- The "reset" button (with the recycling symbol) was resetting the values in the property grid, but not redrawing the mask.
- Carey mask now renders properly, but takes a few seconds.  All those rounded ends = lots and lots of geometry. Be aware that negative "slot adjustment" values are not advised with the Carey mask.

### 0.0.0.1 12/10/2020 

##### Zip File SHA: 90564F0424DDF8AACFC914C9FE67424797C68D1C13E31A4EA2091179E2338B64

### What's Changed From the Web

Everything.  Completely rewritten in C# (original was VB.net), and completely restructured - generation code is now in a separate library and the Windows UI is all new.

Of note to users of the web version: 

- Removed the 72dpi option.  I believe all the scaling issues are resolved by specifying actual units and correctly defining the viewBox attribute on the SVG element.  I have tested in Inkscape, Photoshop, and various DXF viewers, and the measurements seem spot on.

- Fixed some alignment bugs dealing with print margins and crosshairs

- Some really esoteric alignment bugs that will change the amounts entered for "angled slot offset"

- Changed the wording on some of the input parameters:

  - Slot counts => slot limits (values *limit* the # of slots in each quadrant)
  - Edge thickness => Overhang (the amount by which the mask *overhangs* the aperture)
  - Structural bar thickness => StructuralElementWidth (it's a *width*, not a thickness - and it also affects the ring around the knockout, not just structural bars).
  - Open center => HasKnockout - also you can override the knockout diameter

- Additional mask types.  Click the "New Mask" button and be amazed.

  