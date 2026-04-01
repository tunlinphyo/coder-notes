# Cool CSS

## Contents

- [Dotted Blur](#dotted-blur)
- [Text Multi Lines Overflow](#text-multi-lines-overflow)
- [Grid Auto Layout](#grid-auto-layout)
- [Sticky Hack](#sticky-hack)

## Dotted Blur

```css
{
    background-color: rgb(0,0,0);
    background-image: radial-gradient(rgba(0,0,0,0) 1px,
            rgb(0,0,0) 1px);
    background-size: 4px 4px;
    backdrop-filter: brightness(100%) blur(3px);
}
```

## Text Multi Lines Overflow

```css
{
    display: -webkit-box;
    -webkit-line-clamp: 3; /* how many lines */
    -webkit-box-orient: vertical;
    overflow: hidden;
}
```

## Grid Auto Layout

```css
.wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-gap: 1rem;
}

.wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    grid-gap: 1rem;
}
```

## Sticky Hack

Check out the [StickyHack](/script/sticky-hack) class for more advanced usage.

```css
.myElement {
  position: sticky;
  top: -1px;
}

/* styles for when the header is in sticky mode */
.myElement.is-pinned {
  color: red;
}
```

```js
const el = document.querySelector(".myElement")
const observer = new IntersectionObserver(
  ([e]) => e.target.classList.toggle("is-pinned", e.intersectionRatio < 1),
  { threshold: [1] }
);

observer.observe(el);
```
