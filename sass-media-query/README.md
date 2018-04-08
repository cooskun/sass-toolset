# Sass Media Query

## Very Simple and Advanced Media Query to Sass

### query

query is very smart and simple mixin. Just write what you want. It will apply it if you wrote true query and accepts three way.

#### Way 1 : Shortand Queries

```
// Input
@include query(xs) {
    // your codes
}

// Output
@media only screen and (min-width : 320px) {
    // your codes
}
```

##### Other Valid Values

* xs, sm, md, lg, xl
* xs-max, sm-max, md-max, lg-max
* xs-only, sm-only, md-only, lg-only
* portrait, landscape
* retina

It accepts more values than one

```
// Input
@include query(xs, portrait) {
    // your codes
}

// Output
@media only screen and (min-width : 320px) and (orientation : portrait) {
    // your codes
}

// Input
@include query(retina) {
    // your codes
}

// Output
@media only screen and (min--moz-device-pixel-ratio: 1.3), (-o-min-device-pixel-ratio: 2.6 / 2), (-webkit-min-device-pixel-ratio: 1.3), (min-device-pixel-ratio: 1.3), (min-resolution: 1.3dppx) {
    // your codes
}
```

#### Way 2 : CSS Queries

query accepts support from CSS

**Example usage**

```
// Input
@include query((min-width : 320px)) {
    //  your codes
}

// Output
@include query((min-width : 320px), (orientation : portrait)) {
    // your codes
}
```

#### Way 3 : Numeric Values

You can use it with numeric values

**Example usage**

```
// Input
@include query(320px) {
    //  your codes
 }

// Output
@media only screen and (min-width : 320px) {
    // your codes
}

// Input
@include query(320px, 480px) {
    // your codes
}

// Output
@media only screen and (min-width : 320px) and (max-width : 480px) {
    // your codes
}
```

Did you forget write value unit? Don't worry. query will handle it.

```
// Input
@include query(320, 480) {
    //  your codes
}

// Output
@media only screen and (min-width : 320px) and (max-width : 480px) {
    // your codes
}
```

Do you work with 'em' unit or others. Don'be hesitate. You can keep work still with qSass.

```
// Input
@include query(20em) {
    // your codes
}

// Output
@media only screen and (min-width : 20em) {
    // your codes
}
```

---

#### Customize

There is some default values in qSass. You can customize that to yourself.

Just find this object in `_config.scss` and customize the breakpoints. That's all.

```
$Breakpoints : (
    xs : 320px,
    sm : 480px,
    md : 768px,
    lg : 992px,
    xl : 1200px
);
```

Maybe you dont want write your code just for 'only screen'.

```
// You can change follow lines with what you want
$default-device : 'only screen' !default;

// It is for all device types
$default-device : 'all';
```

Also you can make your own query.

```
//  Find the $Queries object in `_config.scss`
//  And write your query to anywhere with a namespace
$Queries : (
    default queries,
    ..............,
    ..............,
    ..............,
    my-custom-query : '(min-width : 1280px) and (max-width : 1920px)'
);

// Now use it
@include query( my-custom-query ) {
    // your codes
}
```

**Note :** Write your query between quotes. It should be string.

### Traversing Mixins

query contains some simple mixins also. Here is the full list:

* sm()
* md()
* lg()
* xl()
* xs-max()
* sm-max()
* md-max()
* lg-max()
* xl-max()
* xs-only()
* sm-only()
* md-only()
* lg-only()
* portrait()
* landscape()
* retina()

**Example Usage**

```
@include xs() {
    //  shortand for query( xs ) {}
}

@include retina() {
    //  your codes
    //  shortand for query(retina)
}
```
