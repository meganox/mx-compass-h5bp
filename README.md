mx-compass-h5bp
===============

Port of H5BP's css to a simple Compass extension.

This module is configured with only a few variables and contains only one mixin
(for the chromeframe), as it's intended for people who want to include H5BP
in full.


Installation
------------

Install as an
[ad-hoc Compass extension] (http://compass-style.org/help/tutorials/extensions/)
by placing in 'extensions' dir in the top level of your project (can be
configured with the 'extensions_dir' directive in your config.rb). A gem may be
available in future.


Usage
-----

### Default H5BP

`@import 'mx-compass-h5bp-top'` at the top of your stylesheet and
`@import 'mx-compass-h5bp-bottom'` at the bottom. `@include 'h5bp-chrome'`
somewhere in your stylesheet. Alternately,

```scss
@import 'mx-compass-h5bp/normalize';
@import 'mx-compass-h5bp/base';
@include 'h5bp-chrome';

/* styles ... */

@import 'mx-compass-h5bp/helpers';
@import 'mx-compass-h5bp/print';
```

This will give you exactly what you would get from the default H5BP css. See
templates/project for a full example (including the example @media section).


### Configuration

The Compass support variables are used to turn on fallbacks for old IE in the
helpers section:

```
$legacy-support-for-ie6: true !default;
$legacy-support-for-ie7: true !default;
```

These are the Compass defaults, the module doesn't set them (in case they
change in future Compass versions).  They have no effect in the normalize
section. I recommend using the compass-normalize plugin instead (I do).

The helpers section is output as Sass pseudo-classes e.g. `%h5bp-invisible` for
use with `@extend` and as HTML classes e.g. `.invisible`. Note that the
pseudo-classes are prefixed. You can suppress the CSS class output by setting
`$h5bp-use-html-classes: false;` if you are only using `@extend`.

The rest of the options control the 'opinioniated defaults' and
chromeframe styling:

```
$h5bp-text-color: #222 !default;
$h5bp-font-size: 1em !default;
$h5bp-line-height: 1.4 !default;
$h5bp-set-font-size: true  !default;
$h5bp-selection-background: #b3d4fc !default;
$h5bp-hr-color: #ccc !default;
$h5bp-chromeframe-background: #ccc !default;
$h5bp-chromeframe-color: #000 !default;
$h5bp-chromeframe-margin: 0.2em 0 !default;
$h5bp-chromeframe-padding: 0.2em 0 !default;
```

Set `$h5bp-set-font-size` to false to disable setting font size on the body element.


### Chromeframe

Chromeframe styling is only included if you include the `h5bp-chrome` mixin.
You can change the classname used by passing it as a parameter.

`@include h5bp-chrome($classname: 'chromey');`
