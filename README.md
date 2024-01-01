% PDF Scripts

A quick hack I threw together for printing out Lego Mario build instructions
PDFs without burning through forty-two cyan toner cartridges.

The [Lego Mario build instructions
PDFs](https://archive.org/details/lego-set-instructions) all have a light blue
background, and for [larger
sets](https://archive.org/details/lego-building-instructions-71391/71391_01_BI_Build_Main/)
there are hundreds of pages.

By running them through `bin/clear-pdf-background`, which detects the
background color on each PDF page and replaces it with transparency, I reduced
the amount of ink consumed to print out copies significantly.

I find that printing the resulting PDF with two pages to a US Letter page
results in sufficiently-readable instructions, while cutting the printed page
count in half.

If your printer supports two-sided printing, that can cut the
number of required pages in half again.


## Caveats

I have only tested this bash script on a NixOS install. It depends on several
CLI tools to do its job.

TODO Declare CLI tools in a .nix file or similar, so it's easier to use.

## License

All works I've created in this repository are under the [CC0 1.0 Universal
license](https://creativecommons.org/publicdomain/zero/1.0/?ref=chooser-v1).

That effectively means "this is in the public domain" (but follow the link for
the legalese if you like).
