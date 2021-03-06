http://wonderweblabs.github.io/curo-material-interface/

Curo Material Interface is an extraction of the wonderweblabs Curo CMS which is used in the client projects (https://curocms.com - soon available). Since we want to reuse the design patterns in other projects, we'll continuously move those implementation in this repo.

Most parts of the implementation are loosely based on the Google Material Design concept (http://www.google.com/design/spec/material-design/introduction.html). Feel free to fork this repo and continue your own interpretation of the google material design concept.

As icon set we use google material design icons (https://github.com/google/material-design-icons).

## Installation

### Middleman & Rails

```ruby
gem 'curo-material-interface'
```

### Include styles

We decided to keep things as open as possible - not like other libraries that include many files by default. Instead, you need to care about the inclusion on your own:

```sass
@import cmi/libs

// !!! Important
// To use curo material interface fonts and icons,
// you need to provide the font-face loading mixin.
@import ./font_mixin

// config
@import cmi/colors
@import cmi/variables
@import cmi/mixins
@import cmi/extensions

// basic curo material interface files
@import cmi/reset
@import cmi/global

// fonts / typo
@import cmi/roboto
@import cmi/icons
@import cmi/typography

// components
@import cmi/components/navbar
@import cmi/components/buttons
@import cmi/components/flex-modal
@import cmi/components/loading-indicator
@import cmi/components/ripples
@import cmi/components/tabs
@import cmi/form_components/text_field
@import cmi/form_components/checkbox
```

At "@import ./font_mixin" you need to implement the right font font-face call for middleman or rails for your application:

**Rails**

```sass
@font-face
 font-family: "Material-Design-Icons"
 src: asset-url("mdi/Material-Design-Icons.eot?-g7cqhn")
 src: asset-url("mdi/Material-Design-Icons.eot?#iefix-g7cqhn") format("embedded-opentype"), asset-url("mdi/Material-Design-Icons.woff?-g7cqhn") format("woff"), asset-url("mdi/Material-Design-Icons.ttf?-g7cqhn") format("truetype"), asset-url("mdi/Material-Design-Icons.svg?-g7cqhn#Material-Design-Icons") format("svg")
 font-weight: normal
 font-style: normal

=font-face-helper($family, $fileBaseName, $weight, $style, $svgAppendix: '')
  @font-face
    font-family: $family
    src: asset-url($fileBaseName + '.eot')
    src: asset-url($fileBaseName + '.eot?#iefix') format('embedded-opentype'), asset-url($fileBaseName + '.woff') format('woff'), asset-url($fileBaseName + '.ttf') format('truetype'), asset-url($fileBaseName + '.svg#' + $svgAppendix) format('svg')
    font-weight: $weight
    font-style: $style
```


**Middleman**

```sass
@font-face
 font-family: "Material-Design-Icons"
 src: font-url("mdi/Material-Design-Icons.eot?-g7cqhn")
 src: font-url("mdi/Material-Design-Icons.eot?#iefix-g7cqhn") format("embedded-opentype"), font-url("mdi/Material-Design-Icons.woff?-g7cqhn") format("woff"), font-url("mdi/Material-Design-Icons.ttf?-g7cqhn") format("truetype"), font-url("mdi/Material-Design-Icons.svg?-g7cqhn#Material-Design-Icons") format("svg")
 font-weight: normal
 font-style: normal

=font-face-helper($family, $fileBaseName, $weight, $style, $svgAppendix: '')
  @font-face
    font-family: $family
    src: font-path($fileBaseName + '.eot')
    src: font-path($fileBaseName + '.eot?#iefix') format('embedded-opentype'), font-path($fileBaseName + '.woff') format('woff'), font-path($fileBaseName + '.ttf') format('truetype'), font-path($fileBaseName + '.svg#' + $svgAppendix) format('svg')
    font-weight: $weight
    font-style: $style
```

### Usage

CMI is completely scoped - meaning that the classes won't work unless you add a container with ```class="cmi"``` somewhere around your implementation. We need that behavior for our cms.

```haml
%body
  // won't work:
  %a.cmi-btn
    My Button

  // works:
  .cmi
    %a.cmi-btn
      My Button
```

The easiest way is to assign cmi class to the body tag, if scoping of the implementation is not important for you:

```haml
%body.cmi
  %a.cmi-btn
    My Button
```
