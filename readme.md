# @kickoff/utils.scss
> Sass Functions and Mixins for the Kickoff framework

[![npm version](https://img.shields.io/npm/v/@kickoff/utils.scss.svg?style=flat-square)](https://www.npmjs.com/package/@kickoff/utils.scss)

## Install

```
npm install @kickoff/utils.scss --save

or

yarn add @kickoff/utils.scss
```

## Usage
With scss and the [npm-sass](https://www.npmjs.com/package/npm-sass) or similar importer like [eyeglass](https://github.com/sass-eyeglass/eyeglass).

```scss
@import "kickoff-utils.scss" // with npm-sass
@import "kickoff-utils" // with eyeglass
```

## Functions

### [_colors.scss](/scss/functions/_colors.scss)
> Various color functions

```scss
// With a color palette map like this:
$color-palette: (
  white: (
    base: #ffffff
  ),

  sky: (
    lighter: #f9fafb,
    light: #f4f6f8,
    base: #dfe3e8,
    dark: #c4cdd5
  )
);

// ko-color() function
a {
  color: ko-color(white); // picks the `base` value
  color: ko-color(sky, dark); // picks the `dark` variant
  color: ko-color(sky, lighter); // picks the `lighter` variant
}

// ko-color-tint() function
// Add percentage of white to a color
a {
  background-color: ko-color-tint(blue, 20%);
}

// ko-color-shade() function
// Add percentage of black to a color
a {
  background-color: ko-color-tint(red, 10%);
}
```

### [_get-value.scss](/scss/functions/_get-value.scss)
> Retrieve value from sass map. Often used within the `font-size` mixin.

```scss
// map helper
ko-getValue(mid, $map) // uses a Sass map
```

### [_get-breakpoint.scss](/scss/functions/_get-breakpoint.scss)
> Get breakpoint from $breakpoints map

```scss
ko-bp(m) // uses the $breakpoints Sass map
```

### [_get-font-family.scss](/scss/functions/_get-font-family.scss)
> Get font-family from $font-family map

```scss
ko-font(system) // uses 'system' font stack
ko-font(sans) // uses the 'sans' font stack
```

### [_get-font-size.scss](/scss/functions/_get-font-size.scss)
> Get font-size from $type map

```scss
ko-font-size(xl) // Kickoff uses t-shirt sizes
ko-font-size(large, $font-sizes) // Using a made-up $font-sizes map
```

### [_get-z-index.scss](/scss/functions/_get-z-index.scss)
> Get z-index value from $z-index map

```scss
ko-zIndex(low) // uses 'low' z-index value
ko-zIndex(mid) // uses 'mid' z-index value
```

### [_map-deep-get.scss](/scss/functions/_map-deep-get.scss)
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

### [_multiply.scss](/scss/functions/_multiply.scss)
> Multiply any value

```scss
ko-multiply(15, 2)
ko-multiply($baseline, 1.5)

// e.g.
a {
	margin-bottom: ko-multiply($baseline, 1.5);
}
```

### [_px-to-em.scss](/scss/functions/_px-to-em.scss)
> Convert px em

For a relational value of 12px write ko-em(12) when the parent is 16px
If the parent is another value say 24px write ko-em(12, 24)

Usage:
```scss
font-size : ko-em(12);
font-size : ko-em(12, 24);
```

### [_strip-units.scss](/scss/functions/_strip-units.scss)
> Strip units

---

## Mixins

### [_type-sizes.scss](/scss/mixins/_type-sizes.scss)
> Type size helper classes based on our [`$type`](https://github.com/TryKickoff/kickoff/blob/master/assets/src/scss/_variables.scss#L32) map. [See demo](https://www.sassmeister.com/gist/4538efbd08b93e5e3478e329f0076321)

```scss
// outputs type-size helpers based on the $type map
// e.g. .u-typeSize--m / .u-typeSize-l
@include ko-type-sizes();

// Using another $map as the 2nd argument would output the above
// as well as the .h1, .h2 values defined in the 2nd $map
@include ko-type-sizes($type, (h1: xxl, h2: xl));

// Using another $map as the 2nd argument would output the above
// as well as the .alpha, .beta values defined in the 2nd $map
@include ko-type-sizes($type, (alpha: xxl, beta: xl));
```

### [_responsive-reveal.scss](/scss/mixins/_responsive-reveal.scss)
> Responsive helper classes to show/hide content based on our [`$breakpoints`](https://github.com/TryKickoff/kickoff/blob/master/assets/src/scss/_variables.scss#L66) map. [See demo](https://www.sassmeister.com/gist/de0fe4e186478fd7defb6cf896665d79)

```scss
@include ko-rwd-reveal();
```

### [_utility.scss](/scss/mixins/_utility.scss)
> Utility Mixins

* clearfix: `@include ko-clearfix;`
* Text truncation: `@include ko-truncate(100%);`
* and a [bunch more](/scss/mixins/utility.scss)

### [_vertical-centre.scss](/scss/mixins/_vertical-centre.scss)
> Vertically center any element. Needs support for CSS tranforms.

```scss
@include vertical-center;
```

### [_hidpi.scss](/scss/mixins/_hidpi.scss)
> Hi-dpi media query mixin

```scss
@include ko-hidpi {
	...
}
```

### [_module-naming-helpers.scss](/scss/mixins/_module-naming-helpers.scss)
> Provides consistent class naming through the usage of mixins

See https://gist.github.com/mrmartineau/0cd2010bf265d712bafb for usage

### [_position.scss](/scss/mixins/_position.scss)
> Position shortcut

```scss
@include ko-position(absolute, 10px 20px 30px 10px);
```

### [_responsive.scss](/scss/mixins/_responsive.scss)
> Responsive media-queries.

**🚨  This is deprecated, we recommend the use of [include-media](http://include-media.com) for media-queries now.**

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

### _units.scss
> Dimension-based mixins

**🚨 These mixins have been removed. They are not needed because we now use a PostCSS plugin ([postcss-pxtorem](https://github.com/cuth/postcss-pxtorem)) that converts px values to rem at the build stage**
