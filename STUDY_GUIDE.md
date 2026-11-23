# SET Days 2026: Study Guide (Kim Cedrick C. Villar, IT-252)

Read this in order. About 30 minutes covers parts 1-5. Use parts 6-9 for practice.

---

## 1. Your 30-second explanation (say this first)

"My website is for SET Days 2026, a campus event at NU Fairview on December 2-4, 2026, where programs compete against each other in sports, esports and other activities. I used NU's navy blue and gold colors. The site is one page, `index.html`, with a CSS file for styling. It has 8 sections linked by IDs in the navigation, a schedule table, lists, an image map on the campus photo, and a footer with a mailto link. All the event details are fictional, and I disclosed my AI use in the README."

**Honest answer if asked about AI:** "I used an AI assistant to help write and debug the code, and I used an AI image generator for the campus pictures. It's disclosed in my README. I reviewed the code and I'm studying it so I can explain it."
Never say you wrote everything alone if you didn't. Being honest is safer.

---

## 2. Files and folders

| File | What it does |
|---|---|
| `index.html` | The whole page: structure and content |
| `css/style.css` | Colors, layout, fonts, spacing, mobile design |
| `images/` | `imagesnu-fairview-campus.png` (venue + image map), `imagesnu-fairview-campus2.png` (hero background), `nu-shield.png` (logo) |
| `README.txt` | Concept, theme, references, AI disclosure |
| `Villar_WEBPROG_SETDays2026.zip` | The submission |

No JavaScript is used. The `js/` folder is empty and not in the ZIP.

**HTML = structure. CSS = looks.** If asked, say HTML says *what* things are (heading, list, table), and CSS says *how they look* (color, size, position).

---

## 3. Page skeleton (top of `index.html`)

```html
<!DOCTYPE html>                 <!-- tells the browser this is HTML5 -->
<html lang="en">                <!-- root element, language is English -->
<head>                          <!-- info about the page, not shown -->
  <meta charset="UTF-8">        <!-- supports all characters -->
  <meta name="viewport" ...>    <!-- makes it work on phones -->
  <title>...</title>            <!-- text on the browser tab -->
  <link rel="stylesheet" href="css/style.css">  <!-- connects the CSS -->
</head>
<body id="top">                 <!-- everything visible; id="top" is for Back to top -->
```

Order of the page inside `<body>`:
`<header>` (nav) -> hero `<section id="home">` -> `<main>` (all other sections) -> `<footer>`

---

## 4. Section by section

### Navigation (`<header><nav>`)
- A logo image + site name linking to `#home`, then a `<ul>` of links.
- **How internal links work:** `<a href="#about">` jumps to the element with `id="about"`. The `#` means "an id on this page".
- Links: `#about`, `#activities`, `#schedule`, `#venue`, `#featured`, `#participate`, `#contact`.

### Home / hero (`id="home"`)
- Title `<h1>` "SET Days 2026", tagline "Rise. Compete. Unite.", intro paragraph, date badge, two buttons.
- Only **one `<h1>`** on the page.
- `<span class="date-badge">` = a small inline piece of text I styled.
- Buttons are really links: `<a class="button" href="#participate">`.
- The hero photo is a **CSS background**, not an `<img>`.

### About (`id="about"`)
- **3 paragraphs** `<p>`, with the dates in `<strong>` (bold, important).
- 3 cards (Purpose, Who Can Join, When and Where), each grouped with a `<div>`. `<br>` makes a line break in "When and Where".
- `<hr>` = horizontal rule, between sections.

### Activities (`id="activities"`)
- `<ul>` unordered (bullet) list with 8 activities, each `<li>`.
- `<ol>` ordered (numbered) list: 5 steps to join.
- `<dl>` description list: `<dt>` = the term, `<dd>` = the definition. Terms: Bracket, Esports, Hackathon, Seeding.

### Schedule (`id="schedule"`)
```html
<table>
  <caption>title of table</caption>
  <thead> <tr><th>Date</th><th>Time</th><th>Activity</th><th>Venue</th></tr> </thead>
  <tbody>
    <tr><td rowspan="2">Dec. 2</td><td>9:00 AM</td>...</tr>
```
- `<tr>` = row, `<th>` = header cell, `<td>` = data cell.
- `<thead>` = header group, `<tbody>` = body group.
- `rowspan="2"` = the date cell stretches down 2 rows. Dec. 2 has 2 rows, Dec. 3 has 3, Dec. 4 has 3. Total: 8 activities.
- `scope="col"` tells screen readers the header applies to a column.

### Venue (`id="venue"`) and image map
```html
<img src="images/imagesnu-fairview-campus.png" width="836" height="470" usemap="#campus-map" alt="...">
<map name="campus-map">
  <area shape="rect" coords="0,160,178,345"  href="#activities"  alt="..." title="...">
  <area shape="rect" coords="180,135,722,345" href="#schedule"    ...>
  <area shape="rect" coords="725,240,836,345" href="#featured"    ...>
  <area shape="rect" coords="0,346,836,470"  href="#participate" ...>
</map>
```
- **Image map** = one picture with several clickable areas.
- `usemap="#campus-map"` on the `<img>` must match `name="campus-map"` on the `<map>`.
- `shape="rect"` = rectangle. `coords="x1,y1,x2,y2"` = left, top, right, bottom corners in **pixels from the top-left of the image**.
- Regions: left wing -> Activities, main building -> Schedule, rooftop garden -> Featured, blue base -> Join.
- The image is a fixed 836x470 so the coordinates stay accurate.
- `alt` = text for screen readers or if the image fails to load.

### Featured (`id="featured"`)
- 3 cards, each a `<div class="feature-card">` with `<h3>`, `<p>` and details.
- `<span class="label">Date:</span> <span class="detail">December 4...</span>`
- `<div>` = a **block** box that groups content (starts on a new line).
- `<span>` = an **inline** wrapper for a piece of text inside a line.

### Participation (`id="participate"`)
- `<ol>` of 5 steps.
- External link: `<a href="https://www.national-u.edu.ph/" target="_blank" rel="noopener">`
  - `target="_blank"` = opens in a new tab.
  - `rel="noopener"` = security best practice for new tabs.
- `<pre>` = preformatted text. It keeps the spaces and line breaks exactly as typed, in a monospace font. Used for the sample confirmation.

### Contact and footer
- Committee cards (fictional names).
- `<a href="mailto:setdays2026@example.com?subject=...">` opens the email app.
- Footer: `<a href="#top">Back to top</a>`, `&copy;` (the copyright symbol), a closing message, and a note that details are fictional.

---

## 5. HTML cheat sheet (the assignment's required elements)

| Element | Meaning | Where I used it |
|---|---|---|
| `<h1>`-`<h3>` | Headings (1 = biggest) | Title, section titles, card titles |
| `<p>` | Paragraph | Everywhere |
| `<a href>` | Link | Nav, buttons, mailto, external |
| `<img>` | Image (no closing tag) | Logo, venue, footer logo |
| `<map>` + `<area>` | Clickable image regions | Venue |
| `<table>` `<tr>` `<th>` `<td>` | Table | Schedule |
| `<ul>` + `<li>` | Bullet list | Featured activities |
| `<ol>` + `<li>` | Numbered list | How to join, participation |
| `<dl>` `<dt>` `<dd>` | Description list | Terms |
| `<hr>` | Horizontal line | Between sections |
| `<br>` | Line break (no closing tag) | "When and Where", featured details |
| `<pre>` | Keeps spacing as typed | Sample confirmation |
| `<div>` | Block container | Cards, groups |
| `<span>` | Inline container | Date badge, labels |
| `<strong>` | Important (bold) text | Dates |

**Attributes** = extra info inside the opening tag, like `name="value"`:
`id`, `class`, `href`, `src`, `alt`, `width`, `height`, `usemap`, `shape`, `coords`, `target`, `rel`, `rowspan`, `scope`, `lang`, `charset`.

- `id` = unique name for one element (used for links, must not repeat).
- `class` = a label used by CSS, can repeat.
- `src` = where an image file is. `href` = where a link goes. `alt` = image description.

**Nesting** = tags inside tags, closed in reverse order: `<ul><li>text</li></ul>`.

**Absolute vs relative paths:** `images/nu-shield.png` is relative (from the HTML file's folder). `https://...` is absolute (full web address).

---

## 6. CSS basics (the parts you should be able to explain)

```css
selector { property: value; }
```
- `:root { --navy: #002060; }` = **variables**. Colors are defined once and reused with `var(--navy)`.
- Colors: **navy `#002060`, blue `#35408e`, gold `#fcd116`** (NU colors).
- `.name` selects a **class**, `#name` selects an **id**, `h2` selects a tag.
- **Box model:** content + `padding` (inside space) + `border` + `margin` (outside space). `box-sizing: border-box` keeps widths predictable.
- `display: flex` = items in a row (the navbar). `display: grid` with `repeat(auto-fit, minmax(240px, 1fr))` = cards that wrap automatically (About, Featured).
- `position: sticky; top: 0` = the nav stays at the top while scrolling.
- `html { scroll-behavior: smooth }` = smooth scrolling to sections.
- `:hover` = style when the mouse is over it (buttons, table rows, nav links).
- Hero background: a navy gradient laid over the campus photo so the text is readable.
- `@media (max-width: 600px) { ... }` = **responsive design**: different styles on small screens.
- `.table-wrap { overflow-x: auto }` = the table scrolls sideways on phones.
- `td[rowspan]` styles only the date cells (gold).
- Fonts: Impact for big titles, Segoe UI for body and small headings.

---

## 7. Likely professor questions (with short answers)

1. **What's the difference between `<div>` and `<span>`?** `div` is block-level (own line), `span` is inline (inside text).
2. **How does your navigation work?** Links use `href="#id"` and each section has the matching `id`.
3. **What's an image map?** An image with clickable regions defined by `<map>` and `<area>`. `usemap` on the image connects to the map's `name`.
4. **What does `coords` mean?** Corner points in pixels measured from the image's top-left. Rectangle is `x1,y1,x2,y2`.
5. **Ordered vs unordered list?** `ol` numbered (order matters, like steps); `ul` bullets.
6. **What is a description list?** `dl` with `dt` (term) and `dd` (definition).
7. **What does `<pre>` do?** Preserves spaces and line breaks, uses monospace font.
8. **What's `rowspan`?** A cell spans several rows. `colspan` is for columns.
9. **Why `alt` on images?** Accessibility and when the image can't load.
10. **Why `target="_blank"`?** Opens in a new tab.
11. **What does `mailto:` do?** Opens the visitor's email app with the address filled in.
12. **Difference between `id` and `class`?** `id` is unique; `class` can be reused.
13. **What's `<head>` vs `<body>`?** Head = information about the page. Body = what's displayed.
14. **What's the `viewport` meta tag for?** Makes the page scale correctly on mobile.
15. **Why one `<h1>`?** It's the main title of the page; it helps structure and SEO.
16. **Block vs inline elements?** Block takes the full line (`p`, `div`, `h1`). Inline stays in the line (`a`, `span`, `strong`).
17. **What does `<br>` do and why no closing tag?** Line break. It's an empty (void) element.
18. **Is the content real?** No. All event details are fictional; the footer and README say so.
19. **Why a hero image if it's not an `<img>`?** It's decoration done in CSS with `background`. The `<img>` tags are the logo and the venue photo.
20. **Did you use JavaScript?** No. HTML and CSS only.

---

## 8. Live-modification practice (the professor may ask you to change things)

Practice each one in `index.html` or `css/style.css` **without AI**. Open the file in VS Code, change, save, refresh the browser.

| Task | How |
|---|---|
| Change the tagline | Find `<p class="tagline">` and edit the text |
| Add a new activity to the list | Copy one `<li>...</li>` inside the `<ul class="activity-list">` and edit it |
| Add a row to the schedule | Copy a `<tr>...</tr>` inside `<tbody>`, edit the cells. If the day uses `rowspan`, increase that number by 1 |
| Add a new term to the description list | Add a `<dt>Term</dt>` and a `<dd>Meaning</dd>` inside the `<dl>` |
| Add a new nav link | Add `<li><a href="#id">Name</a></li>` and make sure a section has that `id` |
| Add a 5th image-map region | Add `<area shape="rect" coords="x1,y1,x2,y2" href="#id" alt="...">` inside `<map>` |
| Change an image-map link | Change the `href` of one `<area>` |
| Change the main color | In `:root`, change `--gold` or `--navy`. Everything updates |
| Make the table border visible | In CSS add `border: 1px solid black;` to `td` |
| Change the font size of paragraphs | Add `p { font-size: 18px; }` |
| Change button hover color | Edit `.button:hover { background: ... }` |
| Add a horizontal line | `<hr>` between two sections |
| Add a new external link | `<a href="https://..." target="_blank">text</a>` |
| Change the email | Edit the `mailto:` link's `href` and text |
| Add a picture | `<img src="images/file.png" alt="description">` |
| Make a list ordered | Change `<ul>`/`</ul>` to `<ol>`/`</ol>` (both tags!) |

**Common mistakes to avoid:** forgetting a closing tag, mismatching `id`/`href`, wrong file path or spelling in `src`, missing quotes around attribute values.

**Tip:** if something doesn't update, press **Ctrl+F5** (hard refresh). If it breaks, press **Ctrl+Z** in the editor.

---

## 9. Demo flow (about 3-5 minutes)

1. Open `index.html` in the browser. Say your 30-second explanation.
2. Click each nav link to show the internal navigation (IDs).
3. Scroll the About section: 3 paragraphs, dates, purpose, the `<hr>`.
4. Activities: point out `ul`, `ol`, `dl`.
5. Schedule: point out the table and `rowspan`.
6. Venue: **click the image-map regions** to show `<map>` and `<area>`.
7. Featured: show `div` and `span`.
8. Participate: show `ol`, the external link and `<pre>`.
9. Contact: click the `mailto:` link, then **Back to top** in the footer.
10. Open the HTML in VS Code and show a few tags if asked.
11. (Optional) Shrink the browser window to show the responsive layout.

---

## 10. Before you present: checklist

- [ ] Open `index.html` from the folder and make sure the images show
- [ ] Click all 4 image-map regions and all nav links once
- [ ] Hover both hero buttons (text must stay readable)
- [ ] Have the HTML open in your code editor too
- [ ] Know that the email is a placeholder (`example.com`) and the names are fictional
- [ ] Know where the AI disclosure is (bottom of README)
- [ ] ZIP name is `Villar_WEBPROG_SETDays2026.zip`
- [ ] Charge your laptop and copy the project to a USB or cloud as a backup

## 11. If you get stuck during the demo

- "I'm not sure, but I can find it in the code." Then locate it with Ctrl+F.
- Stay calm and explain in your own words. Short and correct beats long and wrong.
- If asked to change something, say what you'll do first ("I'll copy this `<li>` and edit the text") and then do it.
