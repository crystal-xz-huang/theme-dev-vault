## Shorthand Properties

See [shorthand property](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties).

### The `*-top`, `*-bottom`, `*-left`, and `*-right` properties 

Many CSS shorthand properties accept four values to define styles for the **four sides** (top, right, bottom, left) or the **four corners** (top-left, top-right, bottom-left, bottom-right) of a box. 

==These values are applied in a **clockwise order ↻**, starting from the top. ==

```css
/* Apply to all four sides */
padding: 1em;

/* top and bottom | left and right */
padding: 5% 10%;

/* top | left and right | bottom */
padding: 1em 2em 2em;

/* top | right | bottom | left */
padding: 5px 1em 0 2em;

/* Global values */
padding: inherit;
padding: initial;
padding: revert;
padding: revert-layer;
padding: unset;
```

### 4 values: `top` | `right` | `bottom` | `left` (↻ clockwise)

```css
/* top | right | bottom | left */
div {
	padding: 25px 50px 75px 100px;
}
```

is equivalent to ...

```css
div {
	padding-top: 25px;
	padding-bottom: 50px;
	padding-left: 75px;
	padding-right: 100px;
}
```

### 3 values: `top` | `left` and `right` | `bottom`

```css
/* top | left and right | bottom */
padding: 1em 2em 2em;
```

### 2 values: `top` and `bottom` | `left` and `right`

```css
/* top and bottom | left and right */
padding: 5% 10%;
```

## CSS Logical Properties

CSS logical properties define property values not be explicit directions like `top` or `left`, but by their _logical_ direction: `inline` or `block`, and `start` or `end`.

- `*-inline` properties follow the direction of the text (**left and right** for English)
- `*-block` properties intersect it (**top and bottom** for English)
- `*-start` properties apply before the element (**top or left** for English)
- `*-end` properties apply after the element (**right or bottom** for English)

```css
.component {
	margin-block-start: 1em; /* top */
	margin-block-end: 1em; /* bottom */
	margin-inline-start: 2em; /* left */
	margin-inline-end: 2em; /* right */
}
```

or 

```css
.component {
	margin-block: 1em 1em; 
	margin-inline: 2em 2em;
}
```
