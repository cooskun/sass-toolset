# Sass Media Query

## Very Simple and Advanced Media Queries for Sass

### media

**media** is a mixin which is very smart and simple. Accepts various parameters. And, gives meaning all of them. Keywords, numbers, even native CSS media queries. This combination make impossible to missing any query type of CSS.

The plugin has many reserved keyword to use shortly. Just put one of them into **media** mixin and start. By the way, this keywords is extendable by you. I will tell how, later.

For now, let's see what can **media mixin** do.

```scss
// Input
@include media(xs, 767, portrait, (prefers-color-scheme: dark), retina) {
    // styles
}

// Output
@media all and (min-width: 320px) and (max-width : 767px) and (orientation : portrait) and (prefers-color-scheme: dark) and (min--moz-device-pixel-ratio : 1.3), (-o-min-device-pixel-ratio: 2.6/2), (-webkit-min-device-pixel-ratio: 1.3), (min-device-pixel-ratio: 1.3), (min-resolution: 1.3dppx)) {
    // styles
}
```

### Usage

```scss
// Input
@include media(xs) {
    // styles
}

// Output
@media all and (min-width : 320px) {
    // styles
}

// All opinions
// xs, sm, md, lg, xl
// xs-max, sm-max, md-max, lg-max
// xs-only, sm-only, md-only, lg-only
// portrait, landscape
// retina
// dark-mode, light-mode
```

#### Examples

#### min-width

```scss
// Input
@include media(xs) {
    // styles
}
// or
@include min(320px) {
    // styles
}
// or
@include xs() {
    // styles
}

// Output
@media all and (min-width: 320px) {
    // styles
}

// All opinions
// xs, xs(): 320px
// sm, sm(): 576px
// md, md(): 768px
// lg, lg(): 992px
// xl, xl(): 1200px
// min( $value )
```

#### max-width

```scss
// Input
@include media(xs-max) {
    // styles
}
// or
@include max(575px) {
    // styles
}
// or
@include xs-max() {
    // styles
}

// Output
@media all and (max-width: 575px) {
    // styles
}

// All opinions
// xs-max, xs-max(): 575px
// sm-max, sm-max(): 767px
// md-max, md-max(): 991px
// lg-max, lg-max(): 1199px
// max( $value )
```

#### Certain Device

```scss
// Input
@include media(md-only) {
    // styles
}
// or
@media md-only() {
    // styles
}

// Output
@media all and (min-width: 768px) and (max-width: 991px) {
    // styles
}

// All opinions
// xs-only, xs-only(): 320px-575px
// sm-only, sm-only(): 576px-767px
// md-only, md-only(): 768px-991px
// lg-only, lg-only(): 992px-1199px
```

#### Between

```scss
// Input
@include media(sm, md-max) {
    // styles
}
// or
@include between(576px, 991px) {
    // styles
}

// Output
@media all and (min-width: 576px) and (max-width: 991px) {
    // styles
}
```

#### Absolute Size (width and height)

```scss
// Input
@include width(1024px) {
    // styles
}

// Output
@media all and (width: 1024px) {
    // styles
}

// Input
@include height(768px) {
    // styles
}

// Output
@media all and (height: 768px) {
    // styles
}
```

#### Orientation

```scss
// Input
@include media(portrait) {
    // styles
}
// or
@include orientation(portrait) {
    // styles
}
// or
@include portrait() {
    // styles
}

// Output
@media all and (orientation: portrait) {
    // styles
}

// All opinions
// media(portrait), media(landscape)
// orientation(portrait), orientation(landscape)
// portrait(), landscape()
```

##### Retina Screen

```scss
// Input
@include media(retina) {
    // styles
}
// or
@include retina() {
    // styles
}

// Output
@media all and (min--moz-device-pixel-ratio: 1.3), (-o-min-device-pixel-ratio: 2.6 / 2), (-webkit-min-device-pixel-ratio: 1.3), (min-device-pixel-ratio: 1.3), (min-resolution: 1.3dppx) {
    // styles
}
```

#### Dark/Light Mode (Mojave)

```scss
// Input
@include media(dark-mode) {
    //  your codes
}
// or
@include dark-mode() {
    //  your codes
}

// Output
@media all and (prefers-color-scheme: dark) {
    // styles
}

// All opinions
// media(dark-mode), media(light-mode)
// color-scheme(dark), color-scheme(light)
// dark-mode(), light-mode()
```

#### Pure CSS Query

```scss
// Input
@include media((min-width : 320px), (max-width: 768px), (orientation: portrait)) {
    // styles
}

// Output
@media all and (min-width: 320px) and (max-width: 768px) {
    // styles
}
```

#### Numeric Values

```scss
// Input
@include media(320px) {
    //  your codes
}

// Output
@media all and (min-width : 320px) {
    // styles
}

// Input
@include media(320px, 480px) {
    // styles
}

// Output
@media all and (min-width : 320px) and (max-width : 480px) {
    // styles
}
```

**Note :** Numeric values doesn't have to have unit. You can skip it.

#### Numeric Values without Unit

```scss
// Input
@include media(320) {
    //  your codes
}

// Output
@media all and (min-width : 320px) {
    // styles
}

// Input
@include media(320, 480) {
    // styles
}

// Output
@media all and (min-width : 320px) and (max-width : 480px) {
    // styles
}
```

If you prefer to working with any other unit instead of px, you can customize it. Follow the [link](#to-cahnge-unitless-number)

#### Configuration

For any configuration go into _config.scss

##### To Change Breakpoints

```scss
$Breakpoints : (
    xs : 320px,
    sm : 480px,
    md : 768px,
    lg : 992px,
    xl : 1200px
);
```

##### To Change Default Device

```scss
$default-device : 'all' !default;
```

<h4 id="to-cahnge-unitless-number">To change default unit for unitless numbers</h4>

```scss
$default-unit-for-unitless: 'px';
```

##### To Add New Keywords

```scss
$Queries : (
    default queries,
    ..............,
    ..............,
    ..............,
    my-custom-query : '(min-width : 1280px) and (max-width : 1920px)'
);

// Now use it
@include media( my-custom-query ) {
    // styles
}
```

**Note :** Write your query between quotes. It should be string.

### Short Mixins

```scss
@include xs() {}                                            // Device is minimum x-small
@include sm() {}                                            // Device is minimum small
@include md() {}                                            // Device is minimum medium
@include lg() {}                                            // Device is minimum large
@include xl() {}                                            // Device is minimum x-large
@include xs-max() {}                                        // Device is maxumum x-small
@include sm-max() {}                                        // Device is maximum small
@include md-max() {}                                        // Device is maximum medium
@include lg-max() {}                                        // Device is maximum large
@include xs-only() {}                                       // Device is x-small
@include sm-only() {}                                       // Device is small
@include md-only() {}                                       // Device is medium
@include lg-only() {}                                       // Device is large
@include min( $value ) {}                                   // Device is equal or bigger than $value
@include max( $value ) {}                                   // Device is equal or smaller than $value
@include between( $min, $max ) {}                           // Device is between $min and $max
@include orientation( $value: portrait/landscape ) {}       // Device orientation is $value
@include portrait() {}                                      // Device orientation is portrait
@include landscape() {}                                     // Device orientation is landscape
@include retina() {}                                        // Device has retina screen
@include color-schema( $value: dark/light ) {}              // Device preferred color is $value (For Mojave color mode)
@include dark-mode() {}                                     // Device preffered color is dark
@include light-mode() {}                                    // Device preffered color is light
```
