# Epiphyte Mono

> **Randy:**  I work for Epiphyte Corporation, which is designed from the ground
> up to work, not on its own, but as an element in a virtual corporation, kind
> of like&mdash;
>
> **Amy:**  I know what an epiphyte is.
>
> &mdash; <cite>*Cryptonomicon*, by Neal Stephenson</cite>

The Epiphyte Mono font is a clear, easy-to-read font primarily intended for
writing code.  It is based on the
[Liberation Mono](https://pagure.io/liberation-fonts) font and so is metrically
compatible with Courier New.  You can find the TTF files to install on your
computer in the `fonts/` directory, or you can download them in a Zip archive
[here](https://github.com/jdw1996/epiphyte-mono/releases/download/v1.1/epiphyte-mono.zip).

This is my first foray into font design, and it would not be possible if not
for the [BirdFont](https://birdfont.org/) font editor and all the work that
others have put into [Liberation Mono](https://pagure.io/liberation-fonts).

*Please note that while GitHub identifies this repository as hosting
[Brainf***](https://esolangs.org/wiki/Brainfuck) code, the `*.bf` files in the
`src/` directory are actually generated by the
[BirdFont](https://birdfont.org/) font editor, and contain font information.*

## Screenshots

### Overview

![overview](https://user-images.githubusercontent.com/17225098/34446405-ac66d7fa-eca8-11e7-9078-d649d7d2af0d.png)

### Differences from Liberation Mono

![differences from Liberation Mono](https://user-images.githubusercontent.com/17225098/34446408-acc97d56-eca8-11e7-9ac6-3f5ffd0b0ec3.png)

### Similar Characters

![similar characters](https://user-images.githubusercontent.com/17225098/34446406-ac990ffe-eca8-11e7-900a-e1d365bc2248.png)

### Code Examples

![code examples](https://user-images.githubusercontent.com/17225098/34446409-ace78508-eca8-11e7-82a2-60822868bd85.png)

## Building the Font

Building the fonts from the `*.bf` source files requires the following
programs:
* [BirdFont](https://birdfont.org)
* [FontForge](https://fontforge.github.io/en-US/)
* [`ttfautohint`](https://www.freetype.org/ttfautohint/)
* [The `fonttools` Python library](https://github.com/fonttools/fonttools)

You can build the fonts with the following steps:
1. Open each `*.bf` file in BirdFont and select from the menu:
  **Import and Export** > **Export Fonts**.
1. In some cases you may be able to simply use the `*.ttf` files generated by
  BirdFont, however it is recommended that you continue through these steps,
  especially if you want the font files to be Windows-compatible.
1. Open the `*.ttf` files generated by BirdFont in FontForge.  Navigate to
  **Element** > **Font Info**.  Select **OS/2** from the sidebar in the pop-up
  window and go to the **Panose** tab.  Set **Proportion** to **Monospaced**.
  Hit **OK** to close the pop-up window.  Now select all glyphs with
  **Ctrl-a**.  Navigate to **Element** > **Validation** > **Find Problems...**.
  Under the **Random** tab, check the box marked
  **Bitmap/outline advance mismatch**.  Under the **BB** tab, check the box
  marked **Check Advance**.  The text field next to that should already have
  `615` entered in it.  Next, press OK, and glyphs will start appearing one at
  a time; for each of them, select **Fix**.  Once this is done, generate
  `*.ttf` files by navigating to **File** > **Generate Fonts...**.
1. It remains to run `ttfautohint` on each of the four `*.ttf` files produced
  by FontForge.  If the name of one is `unhinted.ttf`, run:
    ```
    $ ttfautohint unhinted.ttf hinted.ttf
    ```
  The new file `hinted.ttf` will be the hinted font file, which is ready to be
  installed.

This process is quite hack-y, and was found through a lot of trial and error
(thanks to GitHub user [flocc](https://github.com/flocc) for help testing on
Windows).  If you have any questions, please do not hesitate to
[open an issue](https://github.com/jdw1996/epiphyte-mono/issues/new) or send me
an email at [jdwinters96@gmail.com](mailto:jdwinters96@gmail.com).
