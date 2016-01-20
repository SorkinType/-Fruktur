# Build Instructions

There are two Source files:

1. Fruktur-Regular.vfb Original Source Files with contour overlaps

2. Fruktur-Regular.ufo Original Source Files with contour overlaps, derived from the vfb with vfb2ufo

Load the SRC/Fruktur-Regular.vfb file in FontLab

Go to File, Generate and select "Win TrueType/OpenType TT" 

Go to File, Generate and select "OpenType PS" and ignore the warning about the UPM

Move the 2 files into the repo

Hint the TTF as follows:

    ttfautohint -l 6 -r 46 -G 0 -x 0 -H 350 -D latn -f none \
      -w g -X "" Fruktur-Regular.ttf Fruktur-Regular-ttfa.ttf;
    mv Fruktur-Regular-ttfa.ttf Fruktur-Regular.ttf;

When finished, save the VFB and quit FontLab, and then regenerate the UFO:

    cd SRC;
    rm -rf Fruktur-Regular.ufo;
    vfb2ufo Fruktur-Regular.vfb;
