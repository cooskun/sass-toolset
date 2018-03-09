# SASS-MODERNIZR

It is basic to tell about sass-modernizr if you have tried [Modernizr](https://modernizr.com) before.

Modernizr gives you many plus to check your browser status against new features. sass-modernizr moves it to your css file.

## Example Usage

```
.wrapper {
  @include modernizr(flexbox) {
    display: flex;
  } 

  @include modernizer(flexbox, false) {
    display: block;

   .column {
      float: left;
    } 
  }
}

//  RESULT
.flexbox .wrapper {
  display: flex;
}

.no-js .wrapper,
.no-flexbox .wrapper {
  display: block;
}

.no-js .wrapper .column,
.no-flexbox .wrapper .column {
  float: left;
}
```

It is possible also having more feature in the query

```
.wrapper {
  @include(flexbox flexwrap) {
    display: flex;
    flex-wrap: wrap;
  }
}

// RESULT
.flexbox.flexwrap .wrapper {
  display: flex;
  flex-wrap: wrap;
}
```
