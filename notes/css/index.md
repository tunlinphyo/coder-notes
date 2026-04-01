# CSS

Check CSS support [Can I use _?](https://caniuse.com/).

## Contents

- [Layer](#layer)
- [Property](#property)
- [Starting Style](#starting-style)
- [Counter Style](#counter-style)
- [Color Mix](#color-mix)

## Layer

[@layer](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer)

```css
@layer reset, openprops, theme, utils, layouts, components, pages;

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;600&display=swap') layer(theme);
@import url("https://unpkg.com/open-props") layer(openprops);

@import url(./utils/reset.css) layer(reset);
@import url(./utils/theme.css) layer(theme);
@import url(./utils/utils.css) layer(utils);

@import url(./utils/copy.css) layer(components);

@layer page {
    color: light-dark(#333, #EEE);
    background: light-dark(#EEE, #000);
}
```

## Property

[@property](https://developer.mozilla.org/en-US/docs/Web/CSS/@property)

```css
@property --rotation {
    syntax: "<angle>";
    inherits: false;
    initial-value: 45deg;
}
```

[Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/@property/syntax)

```css
/* A data type name */
syntax: "<color>";

/* A '|' combinator for multiple data types */
syntax: "<length> | <percentage>";

/* Space-separated list of values */
syntax: "<color>+";

/* Comma-separated list of values */
syntax: "<length>#";

/* Keywords */
syntax: "small | medium | large";

/* Combination of data type and keyword */
syntax: "<length> | auto";

/* Universal syntax value */
syntax: "*";
```

## Starting Style

[@starting-style](https://developer.mozilla.org/en-US/docs/Web/CSS/@starting-style)

Can I use [interpolate-size: allow-keywords;](https://caniuse.com/?search=interpolate-size%3A%20allow-keywords%3B)

```css
:root {
    interpolate-size: allow-keywords;
}
.elem {
    display: none;
    height: 0;
    padding: 0 1rem;
    transition-property: display, height, padding;
    transition-duration: 0.3s;
    transition-behavior: allow-discrete;

    .show {
        display: block;
        height: max-content;
        padding: 1rem;

        @starting-style {
            padding: 0 1rem;
            height: 0;
        }
    }
}
```

## Counter Style

[@counter-style](https://developer.mozilla.org/en-US/docs/Web/CSS/@counter-style)

```css
@counter-style reading-list {
    system: cyclic;
    symbols: "📕" "📗" "📘" "📙" "📓" "📒" "📔";
    suffix: "  ";
}

@counter-style tool-list {
    system: cyclic;
    symbols: "⛏️" "🪓" "🧰" "🔩" "⚙️" "⚖️" "🔬" "⚗️" "🔭" "✏️" "✒️" "🔨" "🛠️" "⚒️" "🔧" "🪛" "🪚" "🗜️";
    suffix: "  ";
}
ul[data-reading-list] {
    list-style-type: reading-list;
}
ul[data-tool-list] {
    list-style-type: tool-list;
}
```

## Color Mix

[color-mix()](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/color-mix)

```css
/* color-mix(in <polar-color-space>, <color>, <color> <percentage>) */
color-mix(in hsl, hsl(200 50 80), coral 80%)
/* color-mix(in <polar-color-space> <hue-interpolation-method>, <color>, <color>) */
color-mix(in lch longer hue, hsl(200deg 50% 80%), coral)

/* color-mix(in <rectangular-color-space>, <color>, <color>) */
color-mix(in srgb, plum, #f00)
/* color-mix(in <rectangular-color-space>, <color> <percentage>, <color> <percentage> */
color-mix(in lab, plum 60%, #f00 50%)

/* color-mix(in <custom-color-space>, <color>, <color>) */
color-mix(in --swop5c, red, blue)
```
