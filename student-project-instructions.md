# Student Project Instructions

Follow these steps in order. You will first finish the original website files. Then you will make separate copies for the layout challenge so your completed original stays intact.

## Before you begin

Have these links from your instructor:

- **GitHub repository:** [Add your GitHub repository link]
- **Revised example website:** [Add the link to your revised website]

You will also need a code editor and a way to preview the website in a browser. Use the preview method recommended by your instructor.

## Part 1: Download the project

1. Open the GitHub repository link provided by your instructor.
2. Click the green **Code** button.
3. Choose **Download ZIP**.
4. When the download finishes, extract or unzip the downloaded file.
5. Open the extracted project folder in your code editor.
6. Confirm that you can find `index.html` and the `assets/css/style.css` file.

Your project should include these important paths:

```text
project-folder/
├── index.html
└── assets/
    └── css/
        └── style.css
```

There may be other folders, such as `images`. Keep the project folders in place so the page can find its images and stylesheet.

## Part 2: Finish the original website

1. Open `index.html` in your code editor.
2. Continue from the point where you left off in class. Type the HTML code yourself. Do not copy and paste the HTML code from another student's work or from the example source.
3. Open `assets/css/style.css`.
4. Continue typing the CSS code yourself. Do not copy and paste the CSS code from another student's work or from the example source.
5. Save both files.
6. Preview `index.html` in a browser.
7. Compare your result carefully with the revised example website linked by your instructor. Check the page from top to bottom, including spacing, colors, text, images, buttons, cards, and how it changes at a narrow screen size.
8. Make corrections in your own HTML and CSS until your result matches the revised example website exactly.

**Checkpoint:** Do not start the layout challenge until your original `index.html` and `style.css` match the revised example website.

## Part 3: Make separate files for the challenge

The challenge must be done in copies. This protects the original website you just completed.

1. In your editor, open `index.html`.
2. Click inside the file and press **Ctrl+A** to select all of its text.
3. Press **Ctrl+C** to copy the selected text.
4. Create a new file named `modified.html` in the project root, next to `index.html`.
5. Open `modified.html` and press **Ctrl+V** to paste the copied HTML. Save the file.
6. Open `assets/css/style.css`.
7. Click inside the file and press **Ctrl+A**, then **Ctrl+C**.
8. Create a new file named `modified.css` inside `assets/css/`, next to `style.css`.
9. Open `modified.css` and press **Ctrl+V** to paste the copied CSS. Save the file.

Your project should now include:

```text
project-folder/
├── index.html                 Original completed website
├── modified.html              Copy to use for the challenge
└── assets/
    └── css/
        ├── style.css          Original completed stylesheet
        └── modified.css       Copy to use for the challenge
```

10. In `modified.html`, find the stylesheet link in the `<head>`. Change its `href` so it points to the copied stylesheet:

```html
<link rel="stylesheet" href="assets/css/modified.css">
```

The original `index.html` should continue to link to `assets/css/style.css`. This keeps the original and challenge versions independent.

11. Save `modified.html`, then open it in your browser using your instructor's preview method. Before changing the layout, check that it looks like the original site. If it does not, check that the new stylesheet link is correct and that `modified.css` is in `assets/css/`.

## Part 4: Complete the layout challenge

Open [layout-challenge.md](layout-challenge.md) and follow its steps. Make every HTML change in `modified.html` and every CSS change in `assets/css/modified.css`.

When you are done, check both versions:

- `index.html` should still match the revised example website.
- `modified.html` should show your challenge layout.
- The challenge layout should display correctly at both wide and narrow screen sizes.

## Before you submit

- [ ] The original website matches the revised example website.
- [ ] I typed the original HTML and CSS myself.
- [ ] `modified.html` and `assets/css/modified.css` are separate copies.
- [ ] `modified.html` links to `assets/css/modified.css`.
- [ ] I completed the layout challenge using only the modified files.
- [ ] Both versions open in the browser without missing styles.
