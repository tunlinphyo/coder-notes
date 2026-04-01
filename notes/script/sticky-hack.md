# StickyHack

The StickyHack class accepts two parameters. The first parameter is required and specifies the class name of the sticky element. The second parameter is optional. If the second parameter is not set, the `.paned` class will be toggled by default.

It currently only works for top sticky elements.

`.sticky { display: sticky }`

## Contents

- [Example Script](#example-script)
- [Example Styles](#example-styles)
- [StickyHack](#stickyhack)
- [Inline Script](#inline-script)
- [Inline Styles](#inline-styles)

## Example Script

```ts
new StickyHack('.sticky')
new StickyHack('.sticky', { class: 'sticked' })
new StickyHack('.sticky', { attr: 'data-sticked' })
new StickyHack('.sticky', { attr: { name: 'data-sticked', values: ['on', 'off'] }})
```

## Example Styles

```css
.sticky {
    padding: 20px;
    background-color: Canvas;
    border: 2px solid Highlight;

    position: sticky;
    top: 50px;
    z-index: 5;

    &.pined {
        background-color: AccentColor;
        color: white;
    }

    @media (min-width: 1120px) {
        top: 0;
    }
}
```

## StickyHack

File: `sticky.ts`

```js
export type StickyHackOptions = {
    class?: string;
    attr?: string | { name: string, values: [string, string] };
}

export class StickyHack {
    private elements: NodeListOf<HTMLElement>
    private stickyMap: WeakMap<HTMLElement, boolean> = new WeakMap()

    constructor(selector: string, private options: StickyHackOptions = {}) {
        this.elements = document.querySelectorAll(selector)

        this.handleScroll = this.handleScroll.bind(this)
        this.listeners()
    }

    distory() {
        window.removeEventListener('scroll', this.handleScroll)
    }

    private listeners() {
        this.toggleClass()
        window.addEventListener('scroll', this.handleScroll)
    }

    private toggleClass() {
        for (const elem of this.elements) {
            const rect = elem.getBoundingClientRect()
            const style = getComputedStyle(elem)
            const topValue = parseFloat(style.top)
            const isPinned = rect.top === topValue

            const previous = this.stickyMap.get(elem)
            if (previous === isPinned) continue

            this.stickyMap.set(elem, isPinned)
            this.toggle(elem, isPinned)
        }
    }

    private handleScroll() {
        this.toggleClass()
    }

    private toggle(elem: HTMLElement, is: boolean) {
        if (this.options.class) {
            elem.classList.toggle(this.options.class, is)
        } else if (this.options.attr) {
            if (typeof this.options.attr === 'string') {
                elem.toggleAttribute(this.options.attr, is)
            } else {
                elem.setAttribute(this.options.attr.name, is ? this.options.attr.values[0] : this.options.attr.values[1])
            }
        } else {
            elem.classList.toggle('pined', is)
        }
    }
}
```

## Inline Script

```ts
type StickyHackOptions = {
    class?: string;
    attr?: string | { name: string, values: [string, string] };
}

class StickyHack {
    private elements: NodeListOf<HTMLElement>
    private stickyMap: WeakMap<HTMLElement, boolean> = new WeakMap()

    constructor(selector: string, private options: StickyHackOptions = {}) {
        this.elements = document.querySelectorAll(selector)

        this.handleScroll = this.handleScroll.bind(this)
        this.listeners()
    }

    distory() {
        window.removeEventListener('scroll', this.handleScroll)
    }

    private listeners() {
        this.toggleClass()
        window.addEventListener('scroll', this.handleScroll)
    }

    private toggleClass() {
        for (const elem of this.elements) {
            const rect = elem.getBoundingClientRect()
            const style = getComputedStyle(elem)
            const topValue = parseFloat(style.top)
            const isPinned = rect.top === topValue

            const previous = this.stickyMap.get(elem)
            if (previous === isPinned) continue

            this.stickyMap.set(elem, isPinned)
            this.toggle(elem, isPinned)
        }
    }

    private handleScroll() {
        this.toggleClass()
    }

    private toggle(elem: HTMLElement, is: boolean) {
        // check WeakMap to toggle here
        if (this.options.class) {
            elem.classList.toggle(this.options.class, is)
        } else if (this.options.attr) {
            if (typeof this.options.attr === 'string') {
                elem.toggleAttribute(this.options.attr, is)
            } else {
                elem.setAttribute(this.options.attr.name, is ? this.options.attr.values[0] : this.options.attr.values[1])
            }
        } else {
            elem.classList.toggle('pined', is)
        }
    }
}

new StickyHack('.sticky')
```

## Inline Styles

```css
.sticky {
    margin-bottom: .5rem;
    padding: 20px;
    background-color: Canvas;
    border: 2px solid Highlight;

    position: sticky;
    top: 50px;
    z-index: 5;

    &.pined {
        background-color: var(--accent-color);
        color: white;
    }

    @media (min-width: 1120px) {
        top: 0;
    }
}
```
