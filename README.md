#MDB Generic Web Project Starter
My personal, general-purpose starting template for web development.

## Contents


### The Obvious

Obviously, there's an index.html, stylesheets, and javascript...

### File Structure

![Project Starter File Structure]()

### CSS Preprocessors

Currently, this starting template uses SASS, and the Bourbon mixin library. Alternatively, it's easy to simply delete the Partials and the SCSS folders in favor of using straight CSS.

### Reset Stylesheet

Included is the Reset Stylesheet by Eric Meyer to reduce browser inconsistencies.

### Javascript

The latest stable jQuery library is included as the main javascript library.

### Modernizr

Modernizr is used to detect old browsers, touch devices, devices without support for javascript, and add CSS accordingly.


## SASS Partials

I generally import 3 partials into the style.scss file.

The [_layout.scss](https://github.com/mattdanielbrown/mdb-generic-web-project-starter/blob/master/partials/_layout.scss) is where I handle media queries. There, I also include a light mixin to build grids on the fly:

```
// breakpoints

$S:     480px;   
$M:     768px;     
$L:     1170px;     

// media queries

@mixin MQ($canvas) {
  @if $canvas == S {
   @media only screen and (min-width: $S) { @content; }
  }
  @else if $canvas == M {
   @media only screen and (min-width: $M) { @content; }
  }
  @else if $canvas == L {
   @media only screen and (min-width: $L) { @content; }
  }
}

// super light grid system

@mixin column($percentage, $float-direction:left) {
  width: 100% * $percentage;
  float: $float-direction;
}
```

 The [_mixin.scss](https://github.com/mattdanielbrown/mdb-generic-web-project-starter/blob/master/partials/_mixins.scss) file is where I store custom mixins. For this template (and as a general principle) I try to keep it very simple. However, mixin organization can vary widely between projects.

 ```
 // center vertically and/or horizontally an absolute positioned element

@mixin center($xy:xy) {
  @if $xy == xy {
    left: 50%;
    top: 50%;
    bottom: auto;
    right: auto;
    @include transform(translateX(-50%) translateY(-50%));
  }
  @else if $xy == x {
    left: 50%;
    right: auto;
    @include transform(translateX(-50%));
  }
  @else if $xy == y {
    top: 50%;
    bottom: auto;
    @include transform(translateY(-50%));
  }
}

// border radius

@mixin border-radius($radius:.25em) {
  border-radius: $radius;
}

// antialiasing mode font rendering

@mixin font-smoothing {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

// clearfix

@mixin clearfix {
  &::after {
    clear: both;
    content: "";
    display: block;
  }
}

// color tint and shade

@function shade(
    $color,
    $percent
  ) {

  @return mix(#000, $color, $percent);
}
@function tint(
    $color,
    $percent
  ) {

  @return mix(#fff, $color, $percent);
}
 ```

 Lastly, variables for colors, fonts, and any other need are handled in [_variables.scss](https://github.com/mattdanielbrown/mdb-generic-web-project-starter/blob/master/partials/_variables.scss).

 ```
 // colors

$color-1: #333333; // main text
$color-2: #62c169; // anchor tags
$color-3: #ffffff; // body background color

// fonts

$primary-font: sans-serif;
 ```
