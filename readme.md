
skeletao
========

"Skeletao" should be considered a scaffold or template for building stylesheets.

It is based on three different projects:

* [{less}][lesscss]: a css preprocessor
* [skeleton][skeleton]: a css responsive boilerplate
* [contao][contao]: a content management system

All three projects are selected by personal taste ;-)


What it is
----------

This is a collection of files for building the css for the [contao cms][contao] using the [{less}][lesscss] preprocessor and the basic style and responsiveness from [skeleton][skeleton].


What it isn't
-------------

It is definitely not a "use this and you've got a beautiful site" thingy.


"Holy Grail Layout" and responsiveness
--------------------------------------

The contao cms layout is build around the ["holy-grail-layout"][holygrail], the skeleton boilerplate on the other hand does specify a grid based system. For skeletao, the grid system was removed and the holy-grail-layout adopted to use breakpoints derived from skeleton.

The holy-grail-layout defines three columns that should be aligned side by side: left (mostly used for navigation), main and right (e.g. for additional info). In skeletao there are the following breakpoints defined:

1. smaller than 550px: all columns appear in full width, one below the other
2. larger than 550px: left and main column appear side by side, right column in full width below
3. larger than 750px: all three columns are aligned next to each other
4. larger than 970px: the content has a width of 960px and is centered

All these measurements are variables, so they are easy to adopt.

For the holy-grail-layout the CSS3 flex box syntax is used in all modern browsers. There is a fallback available for Internet Explorer 10 or lower that still uses the old css float method. Luckily contao provides some browser sniffing by assigning the relevant classes to the body element.


Files
-----

In order of loading:

* `index.less`: 'root'-file, combining all the others
* `_vars.less`: all definitions of variables
* `normalize.css`: element and attribute style-[normalizations][normalize]
* `styles.less`: basic styles, mostly derived from skeleton
* `holy-grail-layout.less`: the adopted holy-grail-layout
* `contao.less`: basic styles for contao
* `_custom.less`: a place for custom styles
* `contao/*`: files showing what *could* be styled in the contao frontend; propably not everything is needed - this is more a kind of a reminder of the structure of different contao elements.

Usage
-----

Mostly only the `_vars.less`, `_custom.less` and `contao/*` files need to be edited. But this is only a rule of thumb.

For development I use this command: `lessc index.less output.css`

For production I change `@media (min-width:` to `@media (min-device-width:` in all files and use the `--clean-css` switch on the `lessc` command: `lessc --clean-css index.less output.css`.


[lesscss]:   http://lesscss.org
[skeleton]:  http://getskeleton.com
[contao]:    http://contao.org
[holygrail]: http://www.alistapart.com/articles/holygrail
[normalize]: http://github.com/necolas/normalize.css
