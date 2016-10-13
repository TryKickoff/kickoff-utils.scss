# kickoff-utils.scss
> Sass Functions and Mixins for the Kickoff framework

[![npm version](https://badge.fury.io/js/kickoff-utils.scss.svg)](https://badge.fury.io/js/kickoff-utils.scss)

[![NPM](https://nodei.co/npm/kickoff-utils.scss.png)](https://nodei.co/npm/kickoff-utils.scss/)

## Install

```
npm install kickoff-utils.scss --save
```

## Usage
With scss and the [npm-sass](https://www.npmjs.com/package/npm-sass) or similar importer

```scss
@import "kickoff-utils.scss"
```

## Functions
### [_get-value.scss](functions/_get-value.scss)
> Retrieve value from sass map

### [_map-deep-get.scss](functions/_map-deep-get.scss)
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

### [_modular-scale.scss](functions/_modular-scale.scss)
> Sizes type using a consistent vertical rythm

```scss
// Used in the kickoff $type sass map variable
ko-modular-scale($font-size-base, -1, $type-scale)
ko-modular-scale($font-size-base, 0, $type-scale)
ko-modular-scale($font-size-base, 1, $type-scale)
```

### [_px-to-em.scss](functions/_px-to-em.scss)
> Convert px em

### [_px-to-rem.scss](functions/_px-to-rem.scss) -
> Convert px rem

### [_strip-units.scss](functions/_strip-units.scss)
> Strip units

### [_tint-shade.scss](functions/_tint-shade.scss)
>

```scss
// Add percentage of white to a color
background-color: ko-tint(blue, 20%);

// Add percentage of black to a color
background-color: ko-shade(blue, 20%);
```

## Mixins

### [_hidpi.scss](mixins/_hidpi.scss)
> Hi-dpi media query mixin

```scss
@include ko-hidpi {
	...
}
```

### [_module-naming-helpers.scss](mixins/_module-naming-helpers.scss)
> Provides consistent class naming through the usage of mixins

See https://gist.github.com/mrmartineau/0cd2010bf265d712bafb for usage

### [_position.scss](mixins/_position.scss)
> Position shortcut

```scss
@include ko-position(absolute, 10px 20px 30px 10px);
```

### [_responsive.scss](mixins/_responsive.scss)
> Responsive media-queries

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

### [_units.scss](mixins/_units.scss)
> Dimension-based mixins

* REM calculation: `@include ko-rem(margin, $font-size-base);`
* REM font-size: `@include ko-font-size(16);`
* REM line-height: `@include ko-line-height(22);`
* EM font-size: `@include ko-font-size-ems(20, 16);`
*

### [_utility.scss](mixins/_utility.scss)
> Utility Mixins

* clearfix: `@include ko-clearfix;`
* Text truncation: `@include ko-truncate(100%);`
* and a [bunch more](mixins/utility.scss)

### [_vertical-centre.scss](mixins/_vertical-centre.scss)
> Vertically center any element. Needs support for CSS tranforms.

```scss
@include vertical-center;
```
