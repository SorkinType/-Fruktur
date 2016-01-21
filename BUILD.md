# Build Instructions

There are two Source files:

1. Fruktur-Regular.vfb v1.003 and earlier file, with contour overlaps

2. Fruktur-Regular.ufo v1.004 file, derived from the vfb with vfb2ufo and then developed with Glyphs

Load the SRC/Fruktur-Regular.ufo file in Glyphs

When all your changes are complete, save the UFO with the same filename.

Go to File, Export and select 'Remove Overlap' and 'Autohint', and select this directory to output.

Go to File, Export and select 'Remove Overlap' and 'Autohint' and 'Save as TTF', and select this directory to output.

Hint the TTF as follows:

    ttfautohint -l 6 -r 46 -G 0 -x 0 -H 350 -D latn -f none \
      -w g -X "" Fruktur-Regular.ttf Fruktur-Regular-ttfa.ttf;
    mv Fruktur-Regular-ttfa.ttf Fruktur-Regular.ttf;

Fix up the `name` table with fontbakery:

    fontbakery-fix-nameids.py --autofix Fruktur-Regular.ttf;
    mv Fruktur-Regular.ttf Fruktur-Regular.ttf.fix;

Finally, regenerate the TTX files:

    rm TTX/*/*ttx;
    ttx -s -o TTX/OTF/Fruktur-Regular.ttx Fruktur-Regular.otf;
    ttx -s -o TTX/TTF/Fruktur-Regular.ttx Fruktur-Regular.ttf;

