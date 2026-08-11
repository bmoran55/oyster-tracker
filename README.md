# Northern Neck VA Oyster Garden — site

A 4-page static site (Home, Cohorts, Blog, Donate) for tracking an oyster
garden's cohorts on the Potomac. Pure HTML/CSS + a little vanilla JS —
no build step, no framework, so it works as-is on GitHub Pages.

## File map

```
index.html          Home
cohorts.html         Cohorts index (summary + links to each cohort)
cohort-2025.html      Cohort 2025 detail (2 sample updates)
cohort-2026.html      Cohort 2026 detail (2 sample updates)
blog.html            Blog (4 sample posts, full text)
donate.html          Donate (links out to oystergardener.org/donate)
css/style.css        All styling (design tokens live at the top)
js/main.js           Mobile nav toggle, active-link highlight, scroll reveal
images/              All photos — see "Swapping in your own photos" below
```

## Publishing to GitHub Pages

1. Create a new GitHub repository (or use an existing one) and push this
   folder's contents to the root of the `main` branch.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`,
   branch `main`, folder `/ (root)`. Save.
4. GitHub will give you a URL like `https://yourusername.github.io/repo-name/`
   within a minute or two.

No build tools, no `npm install` — it's ready to serve as-is.

## Swapping in your own photos

Every image in `images/` is a generated placeholder labeled with exactly
what should replace it (e.g. "Add photo: 2025 cohort hero shot") and its
own file path. **Keep the same filename and folder**, and your photo will
drop right in — no HTML edits needed. For example, to replace the June 2025
update's second photo, just overwrite:

```
images/cohort-2025/update1-02.jpg
```

with your own photo, keeping the same filename. Any standard photo editor
or `cp your-photo.jpg images/cohort-2025/update1-02.jpg` on the command
line works. Images are shown at roughly a 4:3 crop, so photos close to that
ratio will look best.

## Adding a new cohort update

Each update on a cohort page lives inside `.timeline` as a repeating pair:
a `.timeline-rail` (the date marker) and a `.update-block` (the content).
Copy an existing update block, update the date, data, notes, and photos,
and give it a new `id` (e.g. `id="update-2026-10"`) so it can be linked to
directly (`cohort-2026.html#update-2026-10`).

## Adding a new cohort (e.g. 2027)

1. Copy `cohort-2025.html` to `cohort-2027.html`.
2. Update the title, hero copy, stats, and update blocks.
3. Add a matching card to `cohorts.html`.
4. Optionally feature its latest update on `index.html`.
5. Make a folder for its photos: `images/cohort-2027/`.

## Adding a new blog post

Copy an `<article class="post">` block in `blog.html`, give it a new `id`,
and add a line to the table of contents (`.post-toc`) at the top of the
page pointing to that `id`.

## Notes

- The donate button and footer link both point to
  `https://www.oystergardener.org/donate` per your request — this site
  does not collect donations itself.
- Colors, fonts, and spacing are all defined as CSS custom properties at
  the top of `css/style.css` under `:root`, so the whole palette can be
  retuned from one place if needed.
