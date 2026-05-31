# CSS Positioning Notes

CSS `position` controls how an element is placed in the layout. It works together with `top`, `right`, `bottom`, `left`, and `z-index`.

## 1. `static`

`static` is the default value. The element stays in the normal document flow.

```css
.box {
  position: static;
}
```

Notes:

- `top`, `right`, `bottom`, and `left` do not affect a static element.
- Most elements use `static` unless you change it.

## 2. `relative`

`relative` keeps the element in the normal flow, but you can shift it from its original spot.

```css
.box {
  position: relative;
  top: 20px;
  left: 10px;
}
```

Notes:

- The original space is still reserved.
- Often used as a parent for absolutely positioned children.

## 3. `absolute`

`absolute` removes the element from the normal flow and positions it relative to the nearest positioned ancestor.

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  right: 0;
}
```

Notes:

- If no positioned ancestor exists, it positions relative to the page or initial containing block.
- The element no longer takes up space in the layout.

## 4. `fixed`

`fixed` positions an element relative to the browser window.

```css
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
```

Notes:

- The element stays in the same place while scrolling.
- Common for headers, floating buttons, and popups.

## 5. `sticky`

`sticky` behaves like `relative` until a scroll threshold is reached, then it acts like `fixed`.

```css
.section-title {
  position: sticky;
  top: 0;
}
```

Notes:

- Works only when the element has a scrollable container.
- `top`, `bottom`, `left`, or `right` must be set for sticky to work properly.

## Important Terms

### Containing block

The containing block is the reference area used to position an element. For `absolute`, it is usually the nearest ancestor with `position: relative`, `absolute`, `fixed`, or `sticky`.

### Inset properties

`top`, `right`, `bottom`, and `left` are called inset properties. They control how far an element is placed from the edges of its containing block.

### `z-index`

`z-index` controls stacking order when elements overlap.

```css
.box1 {
  position: relative;
  z-index: 2;
}

.box2 {
  position: relative;
  z-index: 1;
}
```

Notes:

- `z-index` works on positioned elements.
- Higher values appear on top of lower values.

## Quick Comparison

- `static`: normal flow, no offset control.
- `relative`: stays in flow, can be shifted.
- `absolute`: removed from flow, positioned against a parent.
- `fixed`: pinned to the viewport.
- `sticky`: switches between relative and fixed while scrolling.

## Best Practices

- Use `relative` on a parent when you want to place a child with `absolute`.
- Use `fixed` for elements that must stay visible during scroll.
- Use `sticky` for section headings or navigation bars inside scroll areas.
- Avoid using `absolute` for entire page layout unless you really need it.

## Practice Idea

Try building these in `index.html`:

- A card with an absolutely positioned badge.
- A fixed navbar.
- A sticky section heading.
- A relative box shifted with `top` and `left`.

## Summary

CSS positioning helps control where elements appear on the page. The most important rule is to understand whether an element stays in the normal flow or is removed from it.
