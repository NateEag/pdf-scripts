% PDF Scripts

A quick hack I threw together for printing out Lego Mario build instructions
PDFs without burning through forty-two cyan toner cartridges.

The [Lego Mario build instructions
PDFs](https://archive.org/details/lego-set-instructions) all have a light blue
background, and for [larger
sets](https://archive.org/details/lego-building-instructions-71391/71391_01_BI_Build_Main/)
there are hundreds of pages.

By running them through `bin/clear-pdf-background`, which detects the
background color on each PDF page and replaces it with transparency, I
significantly reduced the amount of ink required to print out the instructions.

I find that printing the resulting PDF with two pages to a US Letter page
results in sufficiently-readable instructions, while cutting the printed page
count in half.

If your printer supports two-sided printing, that can cut the
number of required pages in half again.


## Caveats

I have only tested this bash script on a NixOS install. It depends on several
CLI tools to do its job.

TODO Declare required CLI tools in a .nix file or similar, so it's easier to
use.

TODO Add a progress meter, so there's a reasonable way to tell how the script
is doing.

TODO Add some kind of useful error tracking. I've at least once had a page or
two fail, and then it's an annoying manual process to go back and figure out
which ones failed and manually re-run them (though it's probably my own fault
they failed at all - modifying running bash scripts is a recipe for disaster).
This is why I don't have it cleaning up the tmp directory, because that way
when I discover errors I only have to re-render pages that failed. A good quick
sanity-check before stitching together the final PDF would be that we have the
same number of clarified pages as the original PDF does. If not we could print
out the missing filenames in thhe sequence.

TODO Improve accuracy of color detection and removal against
https://ia802607.us.archive.org/13/items/lego-building-instructions-71369/71369_A_ALT_BI_LOW.pdf.
I hit issues with the blue bricks on the first few pages getting their colors
removed, so I dialed the `fuzziness` parameter back to 5%. That mostly solved
the brick color removal, but resulted in the inset instruction panels retaining
their blue background.

## License

All works I've created in this repository are under the [CC0 1.0 Universal
license](https://creativecommons.org/publicdomain/zero/1.0/?ref=chooser-v1).

That effectively means "this is in the public domain" (but follow the link for
the legalese if you like).
