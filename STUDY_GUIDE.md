# SET Days 2026: Learn Your Own Website

**Kim Cedrick C. Villar, IT-252.** This guide teaches you how your website works from the ground up. You don't need to memorize it. Read each lesson, look at the matching code in `index.html`, and try the "Try it" boxes. By the end you should be able to explain every part in your own words.

**Suggested path (about 90 minutes):**
Lesson 1-3 (20 min) -> Lesson 4-7 (30 min) -> Lesson 8-9 (20 min) -> Practice and quiz (20 min).

---

## Lesson 1: The big picture

A website is a few text files that a browser reads and turns into a page.

| Language | Job | Think of it as | Your file |
|---|---|---|---|
| **HTML** | The content and structure | The **skeleton and body** of a house: walls, rooms, doors | `index.html` |
| **CSS** | The appearance | The **paint, furniture and decoration** | `css/style.css` |
| **JavaScript** | Behavior and reactions | The **electricity**: lights that switch on when you click | *Not used* |

**How the browser reads your site:**
1. You open `index.html`.
2. The browser reads it from top to bottom and builds the page.
3. When it reaches `<link rel="stylesheet" href="css/style.css">`, it loads the CSS and applies the styles.
4. When it reaches an `<img src="...">`, it loads that picture.

**Why no JavaScript?** The assignment says HTML is the main requirement and CSS and JavaScript are optional. Everything required (links, tables, lists, image map) is plain HTML. Less extra code means fewer things to break and explain.

> **Remember:** HTML = *what it is*. CSS = *how it looks*. JavaScript = *what it does*.

---

## Lesson 2: What is an HTML tag, element and attribute?

```html
<a href="#about">About</a>
```

- `<a>` is the **opening tag**. `</a>` is the **closing tag**.
- Everything from the opening to the closing tag is the **element**.
- `href="#about"` is an **attribute**. It gives extra information about the tag. The format is `name="value"`.
- `About` is the **content** the visitor sees.

**Some tags have no closing tag** because they hold no content. They are called *empty* or *void* tags: `<img>`, `<br>`, `<hr>`, `<meta>`, `<link>`, `<area>`.

**Nesting** means putting tags inside other tags. They must close in reverse order, like Russian dolls:

```html
<ul>
  <li>Basketball</li>   <!-- li is INSIDE ul, so li closes first -->
</ul>
```

Wrong: `<ul><li>Basketball</ul></li>` (closed in the wrong order).

**Comments** are notes for humans. The browser ignores them: `<!-- this is a note -->`.

> **Try it:** Open `index.html`, find `<h1>`, change the text, save, and refresh the browser. You just edited HTML.

---

## Lesson 3: The skeleton of your page

Look at the top of `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="...">
  <title>SET Days 2026 | NU Fairview</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body id="top">
  ... everything the visitor sees ...
</body>
</html>
```

| Line | Meaning |
|---|---|
| `<!DOCTYPE html>` | Tells the browser "this is a modern HTML5 page". |
| `<html lang="en">` | The root element that holds everything. `lang="en"` says the page is in English (helps screen readers and translation). |
| `<head>` | **Information about the page.** Nothing here appears on the page itself. |
| `<meta charset="UTF-8">` | Lets the page show all characters correctly, such as the dash in "2-4" and the symbols. |
| `<meta name="viewport" ...>` | Makes the page fit phone screens properly. Without it, phones show a tiny zoomed-out page. |
| `<meta name="description">` | A short summary for search engines. |
| `<title>` | The text on the **browser tab**. |
| `<link rel="stylesheet" href="css/style.css">` | Connects the CSS file. `href` is the file's location. |
| `<body>` | **Everything visible.** |

**head vs body:** head = information *about* the page. body = what the visitor *sees*.

**The order of things inside your `<body>`:**
```
<header>   -> the navigation bar at the top
<section id="home">  -> the big banner (hero)
<main>     -> all the other sections (About, Activities, Schedule, Venue, Featured, Participate, Contact)
<footer>   -> the bottom bar
```

`<header>`, `<nav>`, `<main>`, `<section>` and `<footer>` are **semantic tags**. They look the same as `<div>`, but their names tell you what the part is for. That makes the code easier to read.

---

## Lesson 4: Headings, paragraphs and text

```html
<h1>SET Days 2026</h1>
<h2>About SET Days</h2>
<h3>Purpose</h3>
<p>To promote healthy competition...</p>
<p>The event runs from <strong>December 2 to 4, 2026</strong> at ...</p>
```

- **Headings `<h1>` to `<h6>`:** `h1` is the biggest and most important. Use **only one `<h1>`** per page (the main title). `h2` for section titles, `h3` for sub-titles.
- **Paragraph `<p>`:** a block of text. The browser puts space above and below.
- **`<strong>`:** marks text as important (shown bold).
- **`<br>`:** a line break (drops to the next line without starting a new paragraph). You used it in "When and Where":
  ```html
  <p>December 2&ndash;4, 2026<br>NU Fairview, Quezon City</p>
  ```
- **`<hr>`:** a horizontal line that separates sections. You used it between all major sections, as the assignment requires.
- **`&ndash;`, `&bull;`, `&copy;`:** called **HTML entities**. They make special symbols: `&ndash;` = en dash (-), `&bull;` = bullet, `&copy;` = copyright symbol.

---

## Lesson 5: Links and navigation (very important)

This is worth the most points ("Functional navigation, hyperlinks, and image map": 20 pts).

### 5.1 Internal links (jump within the same page)

**Two pieces work together:**

```html
<!-- THE LINK (in the navbar) -->
<a href="#about">About</a>

<!-- THE DESTINATION (further down the page) -->
<section id="about"> ... </section>
```

- `id="about"` gives that section a **unique name**.
- `href="#about"` says "go to the element whose id is about". The `#` means "look for an id on this page".
- If the spelling doesn't match exactly, the link does nothing.

Your IDs: `top`, `home`, `about`, `activities`, `schedule`, `venue`, `featured`, `participate`, `contact`.

**Back to top** works the same way. The `<body>` has `id="top"` and the footer has `<a href="#top">Back to top</a>`.

### 5.2 External link (to another website)

```html
<a href="https://www.national-u.edu.ph/" target="_blank" rel="noopener">National University website</a>
```
- `href` is the full web address (`https://...`).
- `target="_blank"` opens it in a **new tab**.
- `rel="noopener"` is a safety setting for new tabs.

### 5.3 Email link

```html
<a href="mailto:setdays2026@example.com?subject=SET%20Days%202026%20Inquiry">setdays2026@example.com</a>
```
- `mailto:` opens the visitor's email app with the address already filled in.
- `?subject=...` pre-fills the subject. `%20` means a space.
- `example.com` is a reserved placeholder domain, so this email is fake on purpose.

### 5.4 The difference between a link and a button on your site

The "How to Join" and "View Schedule" **buttons are really links** (`<a>`). CSS makes them look like buttons (class `button`).

> **Try it:** Add a new navigation link. Add `<li><a href="#about">Test</a></li>` to the `<ul>` in the header. Click it. Then change `#about` to `#abot` (a typo) and see that it breaks.

---

## Lesson 6: Lists and tables

### 6.1 Unordered list (bullets): `<ul>`

```html
<ul class="activity-list">
  <li><strong>Basketball Showdown</strong> &ndash; inter-program ... brackets</li>
  <li>...</li>
</ul>
```
- `<ul>` = **u**nordered **l**ist. Each item is an `<li>` (list item).
- Use when the order **doesn't matter**.

### 6.2 Ordered list (numbers): `<ol>`

```html
<ol>
  <li>Choose the activity you want to take part in.</li>
  <li>Gather teammates from your own program...</li>
</ol>
```
- `<ol>` = **o**rdered **l**ist. The browser numbers the items automatically.
- Use when the **order matters** (steps). You have two: How to Join (Activities) and the Participation steps.

### 6.3 Description list: `<dl>`

```html
<dl>
  <dt>Bracket</dt>
  <dd>A chart showing which teams play each other...</dd>
</dl>
```
- `<dl>` = description list. `<dt>` = description **t**erm. `<dd>` = description **d**efinition.
- Use for **term + meaning** pairs, like a glossary. You defined Bracket, Esports, Hackathon and Seeding.

**Quick rule:** bullets -> `ul`. Numbered steps -> `ol`. Term and meaning -> `dl`.

### 6.4 Table: the Schedule

```html
<table>
  <caption>SET Days 2026 Program of Activities</caption>
  <thead>
    <tr>
      <th scope="col">Date</th> <th scope="col">Time</th>
      <th scope="col">Activity</th> <th scope="col">Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">Dec. 2</td>
      <td>9:00 AM</td>
      <td>Opening Program and Parade of Programs</td>
      <td>University Quadrangle</td>
    </tr>
    <tr>
      <td>1:00 PM</td>
      <td>Basketball Showdown: Group Stage</td>
      <td>Gymnasium</td>
    </tr>
    ...
```

| Tag | Meaning |
|---|---|
| `<table>` | The whole table |
| `<caption>` | The table's title |
| `<thead>` | The header **group** (top) |
| `<tbody>` | The body **group** (the rows of data) |
| `<tr>` | **T**able **r**ow |
| `<th>` | **T**able **h**eader cell (bold, for column names) |
| `<td>` | **T**able **d**ata cell (regular cell) |

**`rowspan="2"`** makes one cell stretch down across 2 rows. That's why "Dec. 2" appears once, not twice. **That means the second row of Dec. 2 has no Date cell**, because the first one is covering it. (`colspan` is the same idea for columns.)

Your table: Dec. 2 has 2 rows, Dec. 3 has 3 rows, Dec. 4 has 3 rows. Total: 8 activities.

`scope="col"` tells screen readers the header cell describes a column.

> **Try it:** Add a new row on Dec. 4. Copy the last `<tr>...</tr>`, paste it below, and change the text. Because the Dec. 4 date cell says `rowspan="3"`, change it to `rowspan="4"`, or the new row will shift out of line.

---

## Lesson 7: Images and the image map

### 7.1 Images

```html
<img src="images/nu-shield.png" alt="National University shield logo" width="36" height="36">
```
- `src` = the **file's location** (relative to `index.html`).
- `alt` = **alternative text**: read by screen readers and shown if the image can't load. It must describe the picture.
- `width` / `height` = size in pixels.
- `<img>` has no closing tag.

**Your `<img>` tags (3):** navbar logo, the venue campus photo, and the footer logo. The hero background photo is a **CSS background**, not an `<img>`.

**File paths:** `images/nu-shield.png` is a *relative path*: start from the folder `index.html` is in, go into `images`. In `css/style.css`, the path is `../images/...` because the CSS file is inside the `css` folder, so `../` means "go up one folder first".

### 7.2 The image map (important)

An image map is **one picture with several clickable areas**, each going to a different place.

```html
<img src="images/imagesnu-fairview-campus.png" width="836" height="470"
     usemap="#campus-map" alt="Aerial view of the National University Fairview campus...">

<map name="campus-map">
  <area shape="rect" coords="0,160,178,345"   href="#activities"  alt="..." title="Event Activities">
  <area shape="rect" coords="180,135,722,345" href="#schedule"    alt="..." title="Three-Day Schedule">
  <area shape="rect" coords="725,240,836,345" href="#featured"    alt="..." title="Featured Highlights">
  <area shape="rect" coords="0,346,836,470"   href="#participate" alt="..." title="How to Join">
</map>
```

**How it fits together (3 steps):**
1. The `<img>` has `usemap="#campus-map"`: "use the map called campus-map".
2. The `<map name="campus-map">` has the **same name** (without the `#`). This connects them.
3. Each `<area>` is one clickable region:
   - `shape="rect"` = rectangle.
   - `coords="x1,y1,x2,y2"` = **left, top, right, bottom** corners, in pixels, measured from the **top-left corner of the image** (0,0).
   - `href` = where the click goes.
   - `alt` = text description; `title` = tooltip when you hover.

**Your regions:**
| Part of the photo | Goes to |
|---|---|
| Left wing | Activities |
| Main white building | Schedule |
| Rooftop garden (right) | Featured |
| Blue lower part | Participate (How to Join) |

**Why is the image a fixed 836x470 size?** Coordinates are in pixels. If the image shrank on small screens, the clickable areas wouldn't line up. So it stays fixed, and on phones the area scrolls sideways instead.

**There are also text links under the photo** ("Map guide: left wing -> Activities ...") as a backup.

> **Try it:** Change one `<area>`'s `href` from `#schedule` to `#contact`, refresh, and click the main building. It should now go to Contact.

---

## Lesson 8: div, span and `<pre>`

### `<div>` and `<span>`: containers with no meaning of their own

They exist to **group things** so CSS can style them.

| | `<div>` | `<span>` |
|---|---|---|
| Type | **Block** (takes a full line, starts on a new line) | **Inline** (stays inside a line of text) |
| Use | Group big chunks (a whole card) | Mark a small piece of text |

From your Featured section:
```html
<div class="feature-card">                      <!-- div groups one whole card -->
  <h3>Esports Grand Finals</h3>
  <p>The top two program teams ...</p>
  <p><span class="label">Date:</span> <span class="detail">December 4, 1:00 PM</span><br>
     <span class="label">Venue:</span> <span class="detail">Esports Room</span></p>
</div>
```
The `span`s let CSS color "Date:" gold and make the value bold, without breaking the sentence.

### `<pre>`: preformatted text

```html
<pre>
SET DAYS 2026 - REGISTRATION CONFIRMED
--------------------------------------
Team Name  : Code Bulldogs
...
</pre>
```
Normally HTML squashes extra spaces and ignores line breaks. `<pre>` **keeps your spaces and line breaks exactly as typed** and uses a typewriter-style font. That's why the colons line up in your sample confirmation.

---

## Lesson 9: CSS in simple terms

CSS is a list of rules:
```css
selector { property: value; }
```
Example from your file:
```css
.button { background: var(--gold); color: var(--navy); padding: 10px 22px; }
```
- **Selector** `.button`: *which* elements (all with `class="button"`).
- **Property** `background`: *what* to change. **Value** `var(--gold)`: *to what*.

### Three kinds of selectors
| Selector | Selects | Example |
|---|---|---|
| `h2` | every `<h2>` tag | `h2 { font-size: 2rem; }` |
| `.name` | everything with `class="name"` (can repeat) | `.info-card { ... }` |
| `#name` | the one element with `id="name"` (unique) | |

**id vs class:** an `id` is unique (like a student number). A `class` can be shared (like a section name).

### Colors with variables
At the top of your CSS:
```css
:root {
  --navy: #002060;   /* NU navy */
  --blue: #35408e;
  --gold: #fcd116;   /* NU gold */
}
```
You define a color once, then use `var(--gold)` everywhere. To change the gold, you edit **one line**.

### The box model (how every element takes space)
From inside to outside: **content -> padding -> border -> margin**.
- `padding` = space **inside** the box, around the content.
- `border` = the line around it.
- `margin` = space **outside**, pushing other things away.
- `box-sizing: border-box` makes `width` include padding and border, so sizes are predictable.

### Layout tools you used
- **Flexbox** (`display: flex`): puts items in a **row**. Your navbar uses it (logo on the left, links on the right).
- **Grid** (`display: grid`): rows and columns. Your cards use:
  `grid-template-columns: repeat(auto-fit, minmax(240px, 1fr))`
  = "fit as many columns of at least 240px as you can". On a phone they stack into one column automatically.
- `max-width: 1100px; margin: 0 auto;` = keeps content to a readable width and **centers** it.
- `position: sticky; top: 0` = the navbar sticks to the top when you scroll.
- `scroll-behavior: smooth` = smooth scrolling when you click a link.

### Hover and responsive design
- **`:hover`** = a style that applies only while the mouse is over it:
  ```css
  .button:hover { background: #fff; }
  .nav-links a:hover { color: var(--gold); }
  ```
- **Responsive design** = works on different screen sizes:
  ```css
  @media (max-width: 600px) { h2 { font-size: 1.6rem; } }
  ```
  "Only when the screen is 600px wide or less, make `h2` smaller." Plus `.table-wrap { overflow-x: auto; }` lets the table scroll sideways on phones.

### The hero banner
```css
.hero { background: linear-gradient(...navy fade...), url("../images/imagesnu-fairview-campus2.png") center / cover no-repeat; }
```
A navy gradient is laid **over** the campus photo, so the white text stays readable. `cover` makes the photo fill the area.

### Fonts
Impact for the big titles (h1, h2). A cleaner bold font (Segoe UI) for the small headings (h3) because Impact was hard to read at small sizes.

---

## Lesson 10: What each section does (quick tour of the page)

1. **Navbar:** logo, site name, 7 links.
2. **Hero (`#home`):** title, tagline "Rise. Compete. Unite.", intro, the date badge, 2 buttons.
3. **About (`#about`):** 3 paragraphs, dates, purpose, who can join, and 3 info cards.
4. **Activities (`#activities`):** 8 bullet activities, 5 numbered steps, 4 defined terms.
5. **Schedule (`#schedule`):** the 8-row table over Dec. 2, 3, 4.
6. **Venue (`#venue`):** description, campus photo with the 4-region image map.
7. **Featured (`#featured`):** 3 cards (Esports finals, guest speaker, organizations).
8. **Participate (`#participate`):** numbered steps, external link, `<pre>` sample.
9. **Contact (`#contact`):** committee cards, mailto link.
10. **Footer:** logo, Back to top, copyright, closing message, note that details are fictional.

**The concept in one line:** SET Days is **program vs program**. Each program sends one team per event and wins add up toward the overall championship.

---

## Lesson 11: JavaScript (what it is, and why you skipped it)

JavaScript makes pages react to the visitor: a countdown timer, a menu that opens when you tap it, form checking, pop-ups, sliders.

You didn't use it because:
1. The assignment says it's **optional** and grades the HTML (the rubric has no JavaScript points).
2. Everything required works with HTML alone.
3. You must explain your code, so less extra code is safer.

Your site still has some "interactivity" without JavaScript: hover effects and smooth scrolling are CSS, and the links and image map are HTML.

---

## Lesson 12: Your honesty answers

**Is the content real?** No. The schedule, guest speaker, committee names, venues, deadline and email are fictional for the assignment. The footer and README say so.

**Did you use AI?** Yes, and you disclosed it in the README: an AI assistant helped with brainstorming, researching NU's colors, writing and checking the HTML and CSS, and helping you study. An AI image generator made the campus images. The NU logo is the school's logo.

**Suggested wording:** "I used an AI assistant to help build and debug the site and to help me understand the code. I disclosed it in my README. I've been studying it so I can explain it."

---

## Practice 1: Fix-it drills (do these on your own)

Open `index.html` in VS Code. Try each one, refresh the browser, then **undo (Ctrl+Z)**.

1. Change the tagline to something else.
2. Add a 9th activity to the bullet list.
3. Add a new row to the schedule table.
4. Add a fifth term to the description list.
5. Add a new nav link and a matching section with an `id`.
6. Change which section the main-building region of the image map goes to.
7. Add a fifth `<area>` with `coords="0,0,100,100"` and point it to `#contact`.
8. Change `--gold` in the CSS to another color and refresh.
9. Make table cell borders visible: in CSS add `td { border: 1px solid black; }`.
10. Change `<ul>` to `<ol>` (both the opening and closing tag!) and see bullets turn into numbers.

**Common mistakes to avoid:** forgetting a closing tag; id and `href` spelled differently; wrong file path in `src`; missing quotation marks around an attribute value. If the page doesn't update, press **Ctrl+F5**.

---

## Practice 2: Quiz (cover the answers and answer out loud)

1. What is the difference between HTML and CSS?
2. What is an attribute? Give two examples.
3. How does `<a href="#about">` know where to go?
4. Which tag shows the text on the browser tab?
5. What's the difference between `<ul>` and `<ol>`?
6. What do `dt` and `dd` mean?
7. What does `rowspan="3"` do?
8. What is the difference between `th` and `td`?
9. What does `alt` do?
10. How does `usemap` connect to `<map>`?
11. What do the four numbers in `coords="0,160,178,345"` mean?
12. `div` vs `span`?
13. What does `<pre>` do?
14. Why `target="_blank"`?
15. What does `mailto:` do?
16. `id` vs `class`?
17. Name three empty tags (no closing tag).
18. What does the viewport meta tag do?
19. Why is the hero image not an `<img>`?
20. Why didn't you use JavaScript?

### Answers
1. HTML = structure/content; CSS = appearance.
2. Extra info inside a tag, like `href`, `src`, `alt`, `id`, `class`.
3. It looks for the element with `id="about"` on the same page. The `#` means "an id on this page".
4. `<title>`.
5. `ul` = bullets (order doesn't matter); `ol` = numbered (order matters).
6. `dt` = term; `dd` = its definition (inside a `dl`).
7. The cell stretches down across 3 rows.
8. `th` = header cell (column name, bold); `td` = regular data cell.
9. Describes the image for screen readers and shows if the image fails to load.
10. `usemap="#campus-map"` on the image matches `name="campus-map"` on the `<map>`.
11. Left, top, right, bottom corners in pixels from the image's top-left.
12. `div` = block (own line, groups chunks); `span` = inline (inside a line of text).
13. Keeps spaces and line breaks exactly as typed, in a monospace font.
14. Opens the link in a new tab.
15. Opens the visitor's email app with the address filled in.
16. `id` is unique per element; `class` can be reused.
17. `<img>`, `<br>`, `<hr>` (also `<meta>`, `<link>`, `<area>`).
18. Makes the page scale correctly on phones.
19. It's decoration done with CSS `background`. The `<img>` tags are the logo and the venue photo.
20. It's optional in the assignment, and the required items work with HTML alone.

---

## If the professor asks you to change something live

1. Say your plan out loud: "I'll copy this `<li>` and change the text."
2. Make the change, save, and refresh (Ctrl+F5).
3. If it breaks, Ctrl+Z, then check the closing tags and spelling.
4. If you're not sure, say: "I'm not sure, but I'll find it in my code", then use Ctrl+F to search.

Short and correct beats long and wrong. You know this site, and you built it step by step.

---

## Before you present: checklist

- [ ] Open `index.html` and make sure the images show
- [ ] Click all 4 image-map regions and all nav links
- [ ] Hover both hero buttons
- [ ] Keep `index.html` open in your editor too
- [ ] Remember: the email and names are fictional; the AI disclosure is at the bottom of the README
- [ ] The ZIP is `Villar_WEBPROG_SETDays2026.zip`
- [ ] Back up the project (USB or cloud). It's also on GitHub: https://github.com/Ceddrickx/SETDays2026
