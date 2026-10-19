# Mini Challenge: Improve the Services Section

**Time:** 30–45 minutes

**You will practice:** finding HTML by its class, adding a matching element, changing a CSS rule, and checking a responsive layout.

## Your task

Update the services area in your copied website so it has four cards in two columns on a wide screen. Then make one small style change of your choice and check the page on a narrow screen.

This is a practice version of the CarePoint Clinic example. Keep the service you add fictional. Work only in `modified.html` and `assets/css/modified.css`; your completed original stays as it is.

## 1. Open and explore (5 minutes)

Open `modified.html` in your editor and preview it in your browser. In the HTML, find:

```html
<section class="section" id="services">
```

Inside it, find `<div class="service-grid">`. The three `<article class="service-card">` elements inside this `div` make the three cards you see in the browser.

Now open `assets/css/modified.css` and find the `.service-grid` rule. It uses `display: grid` and `grid-template-columns` to arrange those cards.

**Pause and predict:** What do you think will happen if you add another article? What does the `3` mean in `repeat(3, minmax(0, 1fr))`?

## 2. Add a fourth card (10–15 minutes)

In `modified.html`, find the third service card, **Health Education**. Add this new article after its closing `</article>` and before the closing `</div>` for `.service-grid`:

```html
<article class="service-card">
  <img
    class="service-image"
    src="/assets/images/health-education.jpg"
    alt="A clinic information session"
  />
  <div class="card-icon" aria-hidden="true">04</div>
  <h3>Student Example Service</h3>
  <p>A short description for a fictional service created for this exercise.</p>
</article>
```

You can change the heading and description. Keep the `service-card`, `service-image`, and `card-icon` classes so the existing CSS styles the new card. The example reuses an image path already on the page; if that image is unavailable, the colored image area still shows. The `alt` text should describe the image you choose.

Save and refresh the browser. The new card may sit on a second row by itself. That is okay for now.

**Check your HTML:** Is the new article still between the opening and closing tags of `.service-grid`? If it is outside, Grid will not arrange it with the other cards.

## 3. Arrange two columns (10 minutes)

In `assets/css/modified.css`, find this rule:

```css
.service-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 20px;
}
```

Change `repeat(3, ...)` to `repeat(2, ...)`:

```css
grid-template-columns: repeat(2, minmax(0, 1fr));
```

Save and refresh. The four cards should make two columns and two rows. Here, `repeat(2, ...)` asks for two equal columns; `gap: 20px` adds space between cards.

**Pause and predict:** How many rows would five cards make with two columns?

## 4. Make one small style change (5–10 minutes)

Choose one easy change in `modified.css` and preview it. For example:

- In `.service-card`, change `padding: 16px` to `padding: 22px` to give the card contents more room.
- In `.service-image`, change `height: 150px` to `height: 180px` to make the image area taller.
- In `.service-grid`, change `gap: 20px` to `gap: 28px` to increase the space between cards.

Change one value at a time. Notice which part of the page changes, then keep the value you prefer.

## 5. Check the narrow screen (5 minutes)

Find the `@media (max-width: 760px)` section near the bottom of `modified.css`. Inside it, `.service-grid` is set to `grid-template-columns: 1fr`. Leave that rule in place.

Make your browser window narrow (or use its mobile preview) and refresh. The cards should stack in one column. Widen the window again to see the two-column layout.

## More practice: ten follow-up challenges

Challenges 6–15 help you connect what you see in the browser to the HTML and CSS that create it. Do them in order, one at a time. Each takes about 3–5 minutes. Save and refresh after each change, and use only `modified.html` and `assets/css/modified.css`.

### 6. Edit a card in HTML

In `modified.html`, change the heading and description in your new service card. Save and refresh.

**Notice:** Which words changed? Did the card's layout or styling change?

### 7. Find a matching CSS selector

In `modified.css`, find `.service-card h3`. Change its `color` to `var(--color-accent)`. Save and refresh.

**Notice:** Which headings changed? The space in `.service-card h3` means the rule selects `h3` headings inside service cards.

### 8. Adjust card corners

Find the `.service-card` rule and change `border-radius: 12px` to `border-radius: 24px`. Compare the corners, then choose either value to keep.

**Notice:** Did the corners of the image change too? The image has its own border-radius rule.

### 9. Try the box model

In `.service-card`, change `padding: 16px` to `padding: 24px`. Compare the space between the card's edge and its text. Restore 16px or keep your preferred value.

**In your own words:** What does padding add space between?

### 10. Change the card spacing

In `.service-grid`, change `gap: 20px` to `gap: 32px`. Preview at a wide screen, then narrow the browser.

**Notice:** Does the gap apply between rows as well as columns? Does it change the space inside each card?

### 11. Add a checklist item in HTML

Find `<ul class="checklist">` in `modified.html`. Add one more `<li>` with a general preparation reminder, such as:

```html
<li>A note of any questions you want to ask</li>
```

Save and refresh. Keep the reminder general and suitable for this fictional example.

**Notice:** Which CSS rule styles the new item even though you did not add a new CSS rule?

### 12. Style the checklist items

In `modified.css`, find `.checklist li`. Change its `background` from `rgba(255, 255, 255, 0.8)` to `var(--color-white)`. Refresh and compare the list.

**Notice:** The selector has spaces because it targets each `li` inside `.checklist`.

### 13. Trace a navigation link

In `modified.html`, find the Services link in the navigation. Follow its `href` value to the element with the matching `id` in the page. Click the link in your browser to confirm it jumps to that section.

**Try:** Temporarily change `href="#services"` to `href="#contact"`. Click it, observe where it goes, then restore `#services`.

### 14. Check keyboard focus

Use the **Tab** key to move through the links and buttons on the page. Look for the visible outline around the focused item. Find `a:focus-visible` in `modified.css` and change `outline-offset: 4px` to `outline-offset: 8px`.

Use Tab again and compare the outline. This rule helps people who navigate with a keyboard see which link is selected.

### 15. Explain and test a responsive rule

Find the `@media (max-width: 760px)` rule in `modified.css`. In your own words, explain when its styles apply and what `grid-template-columns: 1fr` does for `.service-grid`.

As a quick test, temporarily change `760px` to `500px`. Resize the browser around 500px wide and observe when the cards stack. Restore `760px` afterward.

**Challenge complete:** Tell a partner which HTML change added content, which CSS change affected appearance, and which rule changed the layout for a narrow screen.

## Done when

- [ ] `modified.html` has four service cards inside `.service-grid`.
- [ ] The added card has an image with useful `alt` text, a heading, and a description.
- [ ] `modified.css` displays two columns on a wide screen.
- [ ] The cards stack into one column on a narrow screen.
- [ ] You made and previewed one small CSS change.
- [ ] You completed the follow-up challenges you chose and restored any temporary test values.
- [ ] `index.html` and `assets/css/style.css` remain your completed original.

## Tell a partner or instructor

1. Which HTML element creates one card?
2. Which CSS value controls the number of columns on a wide screen?
3. What does `gap` change?
4. Which CSS rule makes the cards stack on a narrow screen?

## If something looks wrong

- **The new card has no card styling:** Check that it uses `class="service-card"` and is inside `.service-grid`.
- **None of your CSS changes show up:** Check that `modified.html` links to `assets/css/modified.css`, then save and refresh.
- **The page has no images:** Check the image paths and filenames. The colored image area can still appear if an image file is missing.
- **You see one column:** Widen the browser. The narrow-screen rule applies at 760px and below.
