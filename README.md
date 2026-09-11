# Tidewater Oyster Garden — site

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
what should replace it (e.g. "Add photo: cohort 2025, 2026-08-07, photo 1")
and its own file path. **Keep the same filename and folder**, and your
photo will drop right in — no HTML edits needed. Update photos are named
by cohort and date: `update-YYYY-MM-DD-0N.jpg`. For example, to replace
the second photo from the August 7, 2026 update on Cohort 2025, just
overwrite:

```
images/cohort-2025/update-2026-08-07-02.jpg
```

with your own photo, keeping the same filename. Any standard photo editor
or `cp your-photo.jpg images/cohort-2025/update-2026-08-07-02.jpg` on the
command line works. Images are shown at roughly a 4:3 crop, so photos
close to that ratio will look best.

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

## Data notes from the spreadsheet import

The Cohorts pages were populated from `Oyster_working_data_for_AI.xlsx`
(2025 and 2026 tabs). A few things were flagged rather than silently
corrected, worth checking against your original records:

- **Two date typos, corrected on the site:** Cohort 2025's first entry
  was dated 2026-05-20 in the sheet (should almost certainly be
  2025-05-20, the cohort's start); and one entry was dated 2206-08-07
  (should almost certainly be 2026-08-07). Both are shown corrected,
  with a note on the August 7 entry.
- **Mortality of "-142"** on Cohort 2025's May 16, 2026 entry isn't a
  meaningful value — it's called out as a data note on that update
  rather than displayed as a stat. The count itself (142, down from 405)
  is shown as recorded.
- **Unit inconsistency:** "Largest Oyster Weight" is recorded in grams
  and "Smallest Oyster Weight" in ounces in the source sheet. Both are
  shown with their sheet-recorded units, but a few smallest-weight
  values (e.g. 31–32 oz, 1–1.25 oz) look like they may actually be grams
  too, given how they compare to the largest oyster's weight. Flagged
  in-page with a small note; worth double-checking against your scale
  readings.
- **Cohort 2026's largest diameter** dropped from 2⅜ in (Aug 26) to
  1¾ in (Sep 11) — plausible if a different oyster was measured each
  time, but flagged in-page in case it's a transcription slip.

None of these were guessed at or silently fixed — they're shown as
recorded, with the anomaly noted alongside.

## Notes

- The donate button and footer link both point to
  `https://www.oystergardener.org/donate` per your request — this site
  does not collect donations itself.
- Colors, fonts, and spacing are all defined as CSS custom properties at
  the top of `css/style.css` under `:root`, so the whole palette can be
  retuned from one place if needed.
