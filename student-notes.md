# HTML and CSS Notes for the Clinic Visit Guide

These notes explain how `index.html` provides the page content and how `assets/css/style.css` controls its appearance and layout. HTML gives each piece of content a meaning and a place. CSS selects that content and changes its color, size, spacing, position, and behavior.

## 1. How the browser connects the files

In the `<head>` of `index.html`, this line loads the stylesheet:

```html
<link rel="stylesheet" href="/assets/css/style.css">
```

The browser reads the HTML, finds the link, and applies the CSS rules to matching HTML elements. For example, the HTML has `<header class="site-header">`; the CSS rule `.site-header { ... }` selects it. A dot in a CSS selector means “an element with this class.”

The `<meta charset="UTF-8">` line tells the browser how to read characters. The viewport line helps the page fit phone and tablet screens. The title and description provide page information for the browser and search listings.

## 2. HTML page structure

The page follows a useful nesting pattern:

```text
body
├── header.site-header       Brand and navigation links
├── main                     The page's main content
│   ├── section#home         Welcome message, image, and note
│   ├── section#services     Three service cards
│   ├── section#prepare      Preparation text and checklist
│   └── section#contact      Hours, contact details, and notice
└── footer.site-footer       Copyright and back-to-top link
```

Tags such as `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, and `<footer>` describe the job of their contents. They also help assistive technology and other tools understand the page. A `<div>` is a general-purpose container when no more specific meaning is needed.

### Links and page sections

Navigation links use fragment URLs such as `href="#services"`. The browser looks for an element whose `id` is `services` and scrolls to it. The matching section is `<section class="section" id="services">`. IDs should be unique on a page. The CSS adds smooth scrolling and a little space above target sections so headings are not pressed against the top edge.

### Images and alternative text

`<img>` displays an image. Its `alt` text describes the image for people who cannot see it and for situations where the image does not load. The comments marked `IMAGE SLOT` tell an editor which image path can be replaced. The CSS gives the hero and service images a fixed display area and uses `object-fit: cover` to fill that area while cropping excess edges.

### Lists, contact links, and accessibility

`<ul>` and `<li>` make the preparation items a real list. CSS removes the default bullets and draws a checkmark using `li::before`. The phone and email use `tel:` and `mailto:` links, so compatible devices can start a call or email. `aria-label` gives the navigation a clear name; `aria-hidden="true"` hides decorative marks from screen readers. Keyboard users get a visible focus outline from `:focus-visible` rules.

## 3. How the CSS affects each part

### Shared foundation

- `:root` stores reusable values, called custom properties, such as `--color-primary` and `--content-width`. `var(--color-primary)` uses one of those values. Updating a variable can change many parts of the page together.
- `* { box-sizing: border-box; }` makes an element's declared width include its padding and border. This makes sizing easier to predict.
- The `body` rule removes the browser's default outer margin, chooses the font, sets line spacing, text color, and page background.
- The heading and paragraph rules reset some default margins and make headings' lines more compact.
- `a:focus-visible` draws an accent outline when a keyboard user focuses a link.

Padding shorthand reminder: `padding: 18px 116px` means 18px on the top and bottom, and 116px on the left and right. Four values are read clockwise: top, right, bottom, left.

### Header and navigation

`.site-header` uses Flexbox (`display: flex`) to place the logo and navigation in a row. `justify-content: space-between` pushes them toward opposite ends; `align-items: center` lines them up vertically; `gap` leaves space between them. The `nav` is also a flex container, so its links sit in a row and can wrap if needed. The navigation link rules add padding and remove underlines. `:hover` and `:focus-visible` change the link background when hovered or keyboard-focused.

### Welcome section

`.hero` uses Flexbox to arrange its text, image, and note, with spacing between them. `flex-wrap: wrap` allows items to move onto another line if there is not enough room. Its layered background combines a soft radial highlight with the pale green base color. The `clamp()` font sizes grow with the viewport but stop at set minimum and maximum sizes.

`.hero-image` establishes a fixed-height image window. `overflow: hidden` clips image edges to the rounded frame. `.image-label` is positioned over the image because its parent is `position: relative` and the label is `position: absolute`.

`.hero-note` is another small Flexbox row. `.note-mark` uses a tiny one-cell Grid (`display: grid; place-items: center`) to center the “i” inside its circle.

### Service cards

`.service-grid` is a CSS Grid container. It creates three equal columns using `repeat(3, minmax(0, 1fr))` and puts 20px between the cards. Each `<article class="service-card">` becomes one grid item. The card CSS adds its white background, border, rounded corners, and inside spacing. Hovering lifts it slightly and adds a shadow.

`minmax(0, 1fr)` means each column can shrink to zero as needed and otherwise takes an equal share of available space. The `0` minimum helps long content avoid forcing a grid column wider than its container.

### Visit preparation

`.preparation` is a two-column grid: `0.9fr 1.1fr` gives the checklist a little more width than the introductory copy. `align-items: start` aligns both columns at the top. On smaller screens, the media query changes this to one column. Each checklist item is styled as a rounded panel; a pseudo-element (`::before`) adds the checkmark without putting a decorative mark into the HTML.

### Contact area and footer

`.contact-grid` gives the three contact articles equal grid columns and an 18px gap. `.contact-item` styles each article like a card. The `.notice` rule makes the educational disclaimer stand out with an accent-colored left border. The footer uses Flexbox to distribute its three items across the row.

### Smaller screens and motion preferences

The `@media (max-width: 760px)` block applies when the viewport is 760px wide or less. It stacks the header, hero, and footer content, reduces some padding, and changes the service and contact grids to one column. The preparation grid also becomes one column. This is called a responsive layout: the same HTML rearranges to fit different screen sizes.

The `prefers-reduced-motion` media query checks a visitor's device preference. If they request reduced motion, smooth scrolling and most transitions are shortened.

## 4. How to read a CSS rule

```css
.service-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 28px rgba(36, 52, 58, 0.08);
}
```

`.service-card:hover` is the selector: it targets a service card while the pointer is over it. The declarations inside the braces are the changes. Each declaration has a property, a colon, a value, and a semicolon. Here the card moves up 4 pixels and gets a soft shadow.

## 5. Source details to review

These notes describe the files as they currently appear. A few details may be accidental:

- In `.button:hover`, the last declaration is `border: 10px solid var(--color-acc)`. The custom property `--color-acc` is not defined, and the 10px border is much thicker than the normal button border. Check whether this was intended; the preceding `border-color` already sets the hover border color.
- A few visible characters in the HTML and CSS look corrupted: for example, `Â·`, `Mondayâ€“Friday`, and `âœ“`. These are usually caused by text being saved or read with the wrong character encoding. Since the HTML declares UTF-8, save the file as UTF-8 and use the intended characters (or HTML entities such as `&middot;`, `&ndash;`, and `&#10003;`).
- The image paths point to files in an `images` folder. Confirm those files exist when previewing the page; otherwise the browser will show the alternative text or an empty image area.

## 6. Quick vocabulary

| Word | Plain meaning |
| --- | --- |
| Element | One HTML item, such as a heading, image, or section |
| Tag | The angle-bracket text that marks an element, such as `<p>` |
| Attribute | Extra information in an opening tag, such as `class="hero"` |
| Class | A reusable label in HTML, selected in CSS with a dot, like `.hero` |
| ID | A unique page label, selected in CSS with `#`, and usable as a link target |
| Selector | The part of a CSS rule that chooses which elements to style |
| Property | The kind of style to change, such as `color` or `padding` |
| Value | The setting for a property, such as `teal` or `18px` |
| Flexbox | A CSS layout tool often used to arrange items in one direction |
| Grid | A CSS layout tool for rows and columns together |
| Media query | A CSS condition that applies rules for a screen size or user preference |

For the visual Grid reference, open [CSS Grid Cheat Sheet](css-grid-cheat-sheet.html) in a browser.
