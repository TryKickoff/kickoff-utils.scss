# @kickoff/utils.scss
> Sass Functions and Mixins for the Kickoff framework

[![npm version](https://badge.fury.io/js/@kickoff/utils.scss.svg)](https://badge.fury.io/js/kickoff-utils.scss)

[![NPM](https://nodei.co/npm/@kickoff/utils.scss.png)](https://nodei.co/npm/@kickoff/utils.scss/)

## Install

```
npm install @kickoff/utils.scss --save
```

## Usage
With scss and the [npm-sass](https://www.npmjs.com/package/npm-sass) or similar importer like [eyeglass](https://github.com/sass-eyeglass/eyeglass).

```scss
@import "kickoff-utils.scss" // with npm-sass
@import "kickoff-utils" // with eyeglass
```

## Functions
### [_get-value.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_get-value.scss)
> Retrieve value from sass map. Often used within the `font-size` mixin. There are a number of utility functions that make use of this function, see the [source file](functions/_get-value.scss)

### [_map-deep-get.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_map-deep-get.scss)
> Retrieve value from deeply nested sass map

```scss
 $grid-configuration: (
   'columns': 12,
   'layouts': (
     'small': 800px,
     'medium': 1000px,
     'large': 1200px,
   ),
 );

 div {
   font-size: ko-map-deep-get($grid-configuration, 'columns');
   width: ko-map-deep-get($grid-configuration, 'layouts', 'medium');
 }
```

### [_modular-scale.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_modular-scale.scss)
> Sizes type using a consistent vertical rythm

```scss
// Used in the kickoff $type sass map variable
ko-modular-scale($font-size-base, -1, $type-scale)
ko-modular-scale($font-size-base, 1, $type-scale)
ko-modular-scale($font-size-base, 3, $type-scale)


// or using this shorthand, we assume that `$font-size-base` & `$type-scale` are already set somewhere (in Kickoff, they are set in the _variables.scss file):
$font-size-base: 20;
$type-scale: 1.4

ko-ms(-1)
ko-ms(1)
ko-ms(3)

// e.g.
a {
	font-size: @include font-size(ko-ms(3));
}
```

### [_multiply.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_multiply.scss)
> Multiply any value

```scss
ko-multiply(15, 2)
ko-multiply($baseline, 1.5)

// e.g.
a {
	margin-bottom: ko-multiply($baseline, 1.5);
}
```

### [_px-to-em.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_px-to-em.scss)
> Convert px em

For a relational value of 12px write ko-em(12) when the parent is 16px
If the parent is another value say 24px write ko-em(12, 24)

Usage:
```scss
font-size : ko-em(12);
font-size : ko-em(12, 24);
```

### [_px-to-rem.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_px-to-rem.scss) -
> Convert px rem

### [_strip-units.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_strip-units.scss)
> Strip units

### [_tint-shade.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/functions/_tint-shade.scss)
> Add percentage of white or black to a colour

```scss
// Add percentage of white to a color
background-color: ko-tint(blue, 20%);

// Add percentage of black to a color
background-color: ko-shade(blue, 20%);
```

## Mixins

### [_hidpi.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/_hidpi.scss)
> Hi-dpi media query mixin

```scss
@include ko-hidpi {
	...
}
```

### [_module-naming-helpers.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/_module-naming-helpers.scss)
> Provides consistent class naming through the usage of mixins

See https://gist.github.com/mrmartineau/0cd2010bf265d712bafb for usage

### [_position.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/_position.scss)
> Position shortcut

```scss
@include ko-position(absolute, 10px 20px 30px 10px);
```

### [_responsive.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/_responsive.scss)
> Responsive media-queries. **We recommend the use of [include-media](http://include-media.com) for media-queries now.**

```scss
// min-width
// Equivalent to: @media screen and (min-width: 20em) { ... }
@include ko-respond-min(mid) { ... }; // uses the $breakpoints sass-map
@include ko-respond-min(650) { ... }; // converts to px

// max-width
// Equivalent to: @media screen and (max-width: 20em) { ... }
@include ko-respond-min(large) { ... }; // uses the $breakpoints sass-map
@include ko-respond-min(460) { ... }; // converts to px

// min-max-width
// Equivalent to: @media screen and (min-width: 10em) and (max-width: 20em) { ... }
@include ko-respond-min-max(narrow, large) { ... }; // uses the $breakpoints sass-map
@include ko-respond-min-max(460, 900) { ... }; // converts to px
```

### [_units.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/_units.scss)
> Dimension-based mixins

* REM calculation: `@include ko-rem(margin, $font-size-base);`
* REM font-size: `@include ko-font-size(16);`
* REM line-height: `@include ko-line-height(22);`
* EM font-size: `@include ko-font-size-ems(20, 16);`

### [_utility.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/_utility.scss)
> Utility Mixins

* clearfix: `@include ko-clearfix;`
* Text truncation: `@include ko-truncate(100%);`
* and a [bunch more](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/utility.scss)

### [_vertical-centre.scss](https://github.com/TryKickoff/kickoff-utils.scss/blob/master/mixins/_vertical-centre.scss)
> Vertically center any element. Needs support for CSS tranforms.

```scss
@include vertical-center;
```
