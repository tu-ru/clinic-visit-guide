# Mini Challenge: Build a Two-Column Services Layout

## What you will learn

You will add one service card in HTML, arrange the cards into two columns with CSS Grid, and check how the layout responds on a narrow screen.

**Time:** About 15 minutes

**Use your challenge copies:** First follow [Student Project Instructions](student-project-instructions.md). Make HTML changes in `modified.html` and CSS changes in `assets/css/modified.css`. Keep `index.html` and `assets/css/style.css` as your finished original website.

## Step 1: Find the grid container

Open `modified.html` and find the services section. Inside it, look for this opening tag:

```html
<div class="service-grid">
```

The `div` is the parent container. The service cards are its children. In `modified.css`, the `.service-grid` rule turns this parent into a CSS Grid container. Grid arranges the cards; it does not create the cards for you.

**Pause and predict:** How many cards are currently inside this container? How many columns does the CSS currently make?

## Step 2: Add a fourth service card

In `modified.html`, locate the closing `</article>` for the third service card. After it, but before the closing `</div>` for `.service-grid`, type this new article:

```html
<article class="service-card">
  <img class="service-image" src="images/health-education.jpg" alt="Student example service">
  <div class="card-icon" aria-hidden="true">04</div>
  <h3>Student Example Service</h3>
  <p>A short description written by the student for this example card.</p>
</article>
```

You can write a different short description. This is a fictional example card, so do not present it as a real clinic service. The image reuses a path already used by the page; `alt` describes what this card's image represents.

What each part does:

- `<article class="service-card">` groups the content for one complete card. The class connects it to the card styles in CSS.
- `<img>` displays the picture. `class="service-image"` connects it to the image sizing rules, and `alt` provides a text description.
- `.card-icon` displays the number. `aria-hidden="true"` marks this decorative number as unnecessary for screen readers.
- `<h3>` names the service, and `<p>` holds its description.
- `</article>` closes the card. Keep it inside `.service-grid` so Grid can arrange it with the other cards.

Save `modified.html` and preview it. The new card may appear in a new row because the current grid has three columns. That is expected at this step.

**Check your nesting:** The new `<article>` must be before the grid container's closing `</div>`. If you put it after that `</div>`, it will not be a child of the grid.

## Step 3: Change the grid to two columns

Open `assets/css/modified.css` and find the `.service-grid` rule. It currently has three columns, like this:

```css
.service-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 20px;
}
```

Change only the `grid-template-columns` line so it reads:

```css
grid-template-columns: repeat(2, minmax(0, 1fr));
```

The finished rule should look like this:

```css
.service-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 20px;
}
```

Read the new value from the inside out:

- `1fr` means one share of the available width.
- `minmax(0, 1fr)` lets each column shrink if needed and share the available width equally.
- `repeat(2, ...)` creates two columns using that size.
- `gap: 20px` leaves 20px of space between the rows and columns. It does not set the number of columns.

**Predict before previewing:** With four cards and two columns, how many rows should the browser make?

Save `modified.css` and refresh `modified.html` in your browser. Check whether your prediction was correct.

## Step 4: Check the narrow-screen layout

Find the responsive media query near the bottom of `modified.css`. It already contains this rule:

```css
@media (max-width: 760px) {
  .service-grid, .contact-grid { grid-template-columns: 1fr; }
}
```

Keep this rule. When the screen is 760px wide or narrower, `1fr` makes the services use one column. The same four cards should stack vertically. This is responsive design: CSS changes the arrangement to fit the available screen width.

Preview `modified.html` at a wide browser width, then make the browser narrow. If your preview tool has a mobile view, you can use that too.

## Step 5: Explain what happened

Before finishing, answer these questions in your own words:

1. Which element is the Grid container, and which elements are its grid items?
2. Which number in `repeat(2, minmax(0, 1fr))` controls the number of columns?
3. What does `gap: 20px` control?
4. Which rule changes the layout to one column on a narrow screen?
5. Why did adding an `<article>` create another card, while changing the CSS changed where the cards appeared?

## Success checklist

- There are four service `<article>` elements inside `.service-grid` in `modified.html`.
- The new card has an image, a useful `alt` description, a heading, and a short description.
- At a wide screen size, the cards form two columns and two rows.
- At a narrow screen size, the cards stack into one column.
- The spaces between cards remain visible.
- The original `index.html` still matches the revised example website.

## If the layout does not look right

- If the card is not styled, check that `modified.html` still links to `assets/css/modified.css`.
- If the new card is outside the grid, move its `<article>` above the grid's closing `</div>`.
- If the cards still use three columns, check that you changed `.service-grid` in `modified.css`, not `style.css`.
- If the page is narrow, the media query may be active and showing one column. Widen the browser to see the two-column layout.

## Optional experiment

Change `repeat(2, minmax(0, 1fr))` to `repeat(4, minmax(0, 1fr))`. Predict how four cards will fit, then preview the page. Restore the two-column value afterward. What changed about the width of each card?
