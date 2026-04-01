# Script

## Contents

- [getBoundingClientRect](#elementgetboundingclientrect)
- [getClientRects](#elementgetclientrects)
- [getAnimations](#elementgetanimations)
- [getHTML](#elementgethtml)
- [scrollHeight](#elementscrollheight)
- [Pointer Capture](#pointer-capture)

## Element.getBoundingClientRect()

Returns a single DOMRect that represents the entire bounding box of the element.

```js
const rect = element.getBoundingClientRect();
console.log(rect);
```

![getBoundingClientRect](/scripts/element-box-diagram.png)

## Element.getClientRects()

Returns a **collection of DOMRects** (a DOMRectList) and **one for each visual box** (line box or fragment) that the element occupies.

```js
const rects = element.getClientRects();
for (const rect of rects) {
    console.log(rect);
}
```

## Element.getAnimations()

The following code snippet will wait for all animations on Element and its descendants to finish before removing the element from the document.

```js
Promise.all(
    elem.getAnimations({ subtree: true }).map((animation) => animation.finished),
).then(() => elem.remove());
```

## Element.getHTML()

The [getHTML()](https://developer.mozilla.org/en-US/docs/Web/API/Element/getHTML) method of the Element interface is used to serialize an element's DOM to an HTML string.

```js
const options = {
    serializableShadowRoots: false,
    // A boolean value that specifies whether to include
    // serializable shadow roots. The default value is false.
    shadowRoots: []
    // An array of ShadowRoot objects to serialize.
    // These are included regardless of whether they are marked as serializable,
    // or if they are open or closed. The default value is an empty array.
}
getHTML(options)
```

## Element.scrollHeight

Determine if an element has been totally scrolled

```js
Math.abs(element.scrollHeight - element.clientHeight - element.scrollTop) <= 1;
```

## Pointer Capture

`pointerdown` works for all of `mousedown` (mouse), `touchstart` (touch), and `pen down` (stylus) with one unified event.

```js
const box = document.getElementById('box');

box.addEventListener('pointerdown', (e) => {
    // Start receiving all pointer events, even outside the box
    box.setPointerCapture(e.pointerId);
});

box.addEventListener('pointermove', (e) => {
    if (box.hasPointerCapture(e.pointerId)) {
        console.log('Pointer is being tracked:', e.clientX, e.clientY);
    }
});

box.addEventListener('pointerup', (e) => {
    box.releasePointerCapture(e.pointerId);
});
```
