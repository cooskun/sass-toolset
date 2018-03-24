# SASS Utility Generator

## Make and use your own utilities without unrequired libraries

### Usage

SASS Utility Generator has two mixin to creating utilities. Those are generator() and counter(). Add to your working file which you need. The difference is solid. If you are working with numbers choose the counter, otherwise choose the generator.

`@import "sass-utility-generator/generator.scss";`

or

`@import "sass-utility-generator/counter.scss";`

Now you are ready.

#### Generator

@include generator(prefix, property, values, extra options);

**Input**

```
@include generator(d, display, flex grid block);
```

**Output**

```
.d-flex {
  display: flex;
}
.d-grid {
  display: grid;
}
.d-block {
  display: block;
}
```

**Extra Options**

| Option     | Purpose                                              |
| ---------- | ---------------------------------------------------- |
| important  | Gives the result as !important.                      |
| responsive | Creates the utility with prefix of all device types. |

**Input with extra options**

```
@include generator(d, display, flex, important);
@include generator(d, block, center, responsive);
```

**Output with extra options**

```
.d-flex {
  display: flex !important;
}

.d-block {
  display: block;
}

@media all and (min-width: 320px) {
  .xs-d-block {
    text-align: center;
  }
}

@media all and (min-width: 576px) {
  .sm-d-block {
    text-align: center;
  }
}

@media all and (min-width: 768px) {
  .md-d-block {
    text-align: center;
  }
}

@media all and (min-width: 992px) {
  .lg-d-block {
    text-align: center;
  }
}

@media all and (min-width: 1200px) {
  .xl-d-block {
    text-align: center;
  }
}
```

#### Counter

@include counter(prefix, property, values, extra options);

**Input**

```
// Simple Usage

@include counter(mt, margin-top, 10 20 30);

// or

@include counter(mt, margin-top, 10px 20px 30px);
```

**Output**

```
.mt-10 {
  margin-top: 10px;
}
.mt-20 {
  margin-top: 20px;
}
.mt-30 {
  margin-top: 30px;
}

.mt-10px {
  margin-top: 10px;
}
.mt-20px {
  margin-top: 20px;
}
.mt-30px {
  margin-top: 30px;
}
```

It was just an example of simple usage. But still we can make an overview. counter() doesn't need to unit such as px, em. Because when you add unit class names takes it and result is like mt-10px. It doesn't feel good of course you can prefer it as personal. I can't judge :)

In other hand you can prefer the class name without unit but you can change the unit as value. Do you wonder how? Remember that we have extra options.

| Option     | Valid Value/Values | Purpose                                              |
| ---------- | ------------------ | ---------------------------------------------------- |
| important  | important          | Gives the result with !important                     |
| responsive | responsive         | Creates the utility with prefix of all device types. |
| unit       | px, em, rem, "%"   | Selects the unit of value                            |
| filter     | number             | Make filter for output of counter loops              |

**Input with selected unit**

```
@include counter(mt, margin-top, 1 2 3, rem);
```

**Output with selected unit**

```
.mt-1 {
  margin-top: 1rem;
}
.mt-2 {
  margin-top: 2rem;
}
.mt-3 {
  margin-top: 3rem;
}
```

That's all! Now we arrived to main property of counter. Right we said "counter" but still we didn't count any thing. I know that values can be too much when you will create utilities with numeral values. But no worry. counter() can loops that and can eliminate some via filter.

@include generator(prefix, property, "first" to "last");

To is important in here. You have to use it. Otherwise it will be seem just like two values.

**Input: Loop the values**

```
@include counter(mt, margin-top, 1 to 100);
```

**Output: Loop the values**

```
.mt-1 {
  margin-top: 1px;
}
.......
other utilities between 1 and 100
.......
.mt-100 {
  margin-top: 100px;
}
```

Now take time to filter that. @include counter(prefix, property, values, filter);

**Input: Filter the result**

```
@include counter(mt, margin-top, 1 to 100, 10);
```

**Output: Filter the result**

```
.mt-10 {
  margin-top: 10px;
}
.mt-20 {
  margin-top: 20px;
}
...
other utilities between 1 and 100
...
.mt-90 {
  margin-top: 90px;
}
.mt-100 {
  margin-top: 100px;
}
```

Liked? I hope you did. Last tip. You can have much properties than one in the same utility.

**Input**

```
@include counter(mtb, margin-top margin-bottom, 25 50 75 100, "%");
```

**Output**

```
.mtb-25 {
  margin-top: 25%;
  margin-bottom: 25%;
}
.mtb-50 {
  margin-top: 50%;
  margin-bottom: 50%;
}
.mtb-75 {
  margin-top: 75%;
  margin-bottom: 75%;
}
.mtb-100 {
  margin-top: 100%;
  margin-bottom: 100%;
}
```
