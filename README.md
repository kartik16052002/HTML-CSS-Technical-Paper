% HTML and CSS:


## Abstract

This short paper explains the basics of HTML and CSS. It focuses more on CSS Flexbox because Flexbox is a practical and modern layout tool. The HTML section is crisp and the Flexbox section goes into more detail with clear examples you can try.

---

## Introduction

Web pages are built with two main languages: HTML (for structure) and CSS (for style). HTML gives the page elements like headings, paragraphs, and images. CSS decides how those elements look and where they sit on the page.

---

## HTML

HTML stands for HyperText Markup Language. It uses tags to describe parts of a page. Keep HTML simple and semantic: use headings, paragraphs, lists, and correct tags for images and links.

Simple example:

```html
<!doctype html>
<html lang="en">
	<head>
		<meta charset="utf-8">
		<title>Sample</title>
	</head>
	<body>
		<header>
			<h1>Site Title</h1>
		</header>
		<main>
			<p>Hello, this is a short example.</p>
		</main>
		<footer>© 2025</footer>
	</body>
</html>
```

Best practices (short):

- Use semantic tags: `header`, `nav`, `main`, `section`, `article`, `footer`.
- Use meaningful `alt` text for images.
- Keep structure clean; leave layout to CSS.

---

## CSS Basics

CSS controls color, spacing, layout, fonts, and more. A few key ideas:

- Selectors: target elements (e.g., `p`, `.class`, `#id`, `div > p`).
- Box model: each element has `content`, `padding`, `border`, and `margin`.
- Display: `block`, `inline`, `inline-block`, `flex`, `grid`.
- Positioning: `static`, `relative`, `absolute`, `fixed`, `sticky`.
- Mobile-first: write styles for small screens first, then add media queries.

Quick example (box model and display):

```css
.card {
	display: block;
	padding: 16px;     /* inside space */
	border: 1px solid #ddd;
	margin-bottom: 12px; /* outside space */
}
```

---

## Flexbox 

Flexbox is a CSS layout mode that makes it easier to design flexible and responsive layouts. Use it when you need to align items in a row or column, to distribute space, or to reorder items visually.

Why use Flexbox?

- Easy centering both horizontally and vertically.
- Items can grow or shrink to fill available space.
- Reordering content for layout without changing HTML.
- Works well for single-dimensional layouts (row or column).

### Core Concepts

- Flex container: an element with `display: flex` or `display: inline-flex`.
- Flex items: direct children of a flex container.
- Main axis: the direction in which flex items are laid out (row or column).
- Cross axis: perpendicular to the main axis.

### Common Flex Container Properties

- `display: flex` or `inline-flex` — makes the element a flex container.
- `flex-direction` — sets the main axis. Values: `row`, `row-reverse`, `column`, `column-reverse`.
- `flex-wrap` — allows items to wrap: `nowrap`, `wrap`, `wrap-reverse`.
- `flex-flow` — shorthand for `flex-direction` + `flex-wrap`.
- `justify-content` — alignment along the main axis. Values: `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`.
- `align-items` — alignment along the cross axis for all items. Values: `stretch` (default), `flex-start`, `flex-end`, `center`, `baseline`.
- `align-content` — alignment of multi-line content along the cross axis when there is extra space (works when items wrap).
- `gap` — spacing between flex items (supported in modern browsers).

### Common Flex Item Properties

- `order` — controls visual order (default 0). Lower numbers appear first.
- `flex-grow` — how much an item will grow relative to others (default 0).
- `flex-shrink` — how much an item will shrink relative to others (default 1).
- `flex-basis` — the starting size before growth/shrink (can be `auto` or length).
- `flex` — shorthand for `flex-grow`, `flex-shrink`, and `flex-basis`. Example: `flex: 1 0 200px`.
- `align-self` — override `align-items` for a single item.

### Basic Examples

1) Centering an element both ways

```html
<div class="center-box">
	<div class="inner">Centered</div>
</div>
```

```css
.center-box {
	display: flex;
	align-items: center;    /* vertical */
	justify-content: center;/* horizontal */
	height: 200px;
	border: 1px dashed #ccc;
}
.inner { padding: 8px 12px; background:#f6f6f6; }
```

2) Horizontal navigation with space between items

```html
<nav class="nav">
	<a href="#">Home</a>
	<a href="#">About</a>
	<a href="#">Contact</a>
	<a href="#">Blog</a>
</nav>
```

```css
.nav {
	display: flex;
	gap: 16px;
	justify-content: space-between;
	align-items: center;
}
.nav a { text-decoration: none; color:#111; }
```

3) Two-column layout (sidebar + content)

```html
<div class="layout">
	<aside class="sidebar">Sidebar</aside>
	<main class="content">Main content</main>
</div>
```

```css
.layout { display:flex; gap:16px; }
.sidebar { flex: 0 0 240px; /* fixed-ish width */ }
.content { flex: 1; /* take remaining space */ }
```

4) Responsive wrapping gallery

```html
<div class="gallery">
	<div class="item">1</div>
	<div class="item">2</div>
	<div class="item">3</div>
	<div class="item">4</div>
</div>
```

```css
.gallery {
	display:flex;
	flex-wrap:wrap;
	gap:12px;
}
.item {
	flex: 1 1 200px; /* grow and shrink, base 200px */
	min-width: 140px;
	height: 120px;
	background:#eef;
	display:flex; align-items:center; justify-content:center;
}
```

### Practical Patterns and Tips

- Center a single item: use `display:flex; align-items:center; justify-content:center;` on the parent.
- Equal-height columns: set `display:flex` on the row and each column will match the tallest item (use `align-items: stretch`).
- Spacing: prefer `gap` for consistent spacing instead of margins on children.
- Order vs HTML: `order` changes visual order but not the DOM order — screen readers and tab order still follow DOM. Use `order` carefully for accessibility.
- Use `flex: 1` to make items share space equally.
- Avoid using `flex-basis: auto` with non-flexible images without constraints; images may overflow unless constrained by `max-width`.

### Common Mistakes

- Forgetting to set `min-width` or `min-height`: items may shrink too small.
- Mixing `float` and `flex` for the same layout: prefer one approach.
- Relying on `order` to fix logical structure: this can hurt accessibility and keyboard navigation.

### Debugging Flexbox

- Use browser devtools: modern inspectors show flex axes and allow toggling properties.
- Temporarily add background colors or outlines to items to see alignment and spacing.
- Check computed styles for `flex-basis`, `flex-grow`, and `flex-shrink`.

### Browser Support

Flexbox works across modern browsers. For very old browsers, consider graceful fallback or a simple float-based layout. Use `display: -webkit-box` or prefixes only if you must support very old Android or old iOS browsers (rare in 2025).

---

## Useful Examples

- Centering a modal: parent `display:flex; align-items:center; justify-content:center;`.
- Navbar that collapses: use `flex-wrap:wrap` and media queries to change `flex-direction` to `column` on small screens.
- Footer with three columns: `display:flex; gap:20px;` and `flex:1` on child columns.

Code snippet: simple responsive header

```html
<header class="site-header">
	<div class="logo">Logo</div>
	<nav class="main-nav"> ... </nav>
</header>
```

```css
.site-header { display:flex; align-items:center; justify-content:space-between; gap:20px; padding:12px; }
@media (max-width:600px) {
	.site-header { flex-direction:column; align-items:stretch; }
}
```

---

## Conclusion

HTML provides structure. CSS makes structure look good. Flexbox is a powerful, easy-to-use tool for single-axis layouts. It helps solve common layout problems like centering, equal-height columns, and responsive wrapping with minimal code.

---

## References

- MDN Web Docs — CSS Flexible Box Layout: https://developer.mozilla.org/
- CSS Tricks — A Complete Guide to Flexbox: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
