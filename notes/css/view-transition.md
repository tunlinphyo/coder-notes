# View Transition API

Reference: [@view-transition](https://developer.mozilla.org/en-US/docs/Web/CSS/@view-transition), [Open Props](https://open-props.style/)

## Contents

- [Syntax](#syntax)
- [Transition Group](#transition-group)
- [Keyframes](#keyframes)

## Syntax

```css
@view-transition {
    navigation: auto;
}
```

## Transition Group

```css
::view-transition-group(root) {
    animation-duration: .5s;
}

::view-transition-old(root) {
    animation-name: PageOut;
    animation-timing-function: var(--ease-spring-3);
}
::view-transition-new(root) {
    animation-name: PageIn;
    animation-timing-function: var(--ease-spring-1);
}

::view-transition-old(pageTitle) {
    animation-name: TitleOut;
}
::view-transition-new(pageTitle) {
    animation-name: TitleIn;
}

@media (max-width: 991px) {
    ::view-transition-group(aside) {
        animation-duration: .5s;
    }

    ::view-transition-old(aside) {
        animation-name: SlideOut;
        animation-timing-function: var(--ease-spring-1);
    }
}
```

## Keyframes

```css
@keyframes PageIn {
    from {
        translate: 100vw 0;
    }
    to {
        translate: 0 0;
    }
}

@keyframes PageOut {
    from {
        translate: 0 0;
        opacity: 1;
    }
    to {
        translate: -50vw 0;
        opacity: 0;
    }
}

@keyframes TitleIn {
    from {
        translate: 200px 0;
    }
    to {
        translate: 0 0;
    }
}

@keyframes TitleOut {
    from {
        opacity: 1;
    }
    to {
        opacity: 0;
    }
}

@keyframes SlideOut {
    to {
        translate: -110% 0;
    }
}
```
