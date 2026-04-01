# Aria

Make element Aria only.

## Contents

- [Example HTML](#example-html)
- [Styles](#styles)

## Example HTML

```html
<input data-aria-only type="radio" />
```

## Styles

```css
@layout utils {
    [data-aria-only] {
        position: absolute;
        width: 1px;
        height: 1px;
        margin: -1px;
        padding: 0;
        overflow: hidden;
        clip: rect(0, 0, 0, 0);
        white-space: nowrap;
        border-width: 0;
    }
}
```
