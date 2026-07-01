# Hydro Internship — Field Report (GitHub Pages site)

A small multi-page site summarizing an internship at Hydro's Rackwitz site.

## File structure

```
.
├── index.html              ← homepage (hero, stats, links to each phase)
├── gallery.html             ← photo/video archive
├── reflection.html          ← skills & reflection
├── phases/
│   ├── onboarding.html      ← Phase 01
│   ├── extrusion.html       ← Phase 02
│   ├── casthouse.html       ← Phase 03
│   └── handover.html        ← Phase 04
├── assets/
│   ├── style.css            ← shared styles (edit colors/fonts here once, applies everywhere)
│   ├── nav.js                ← mobile menu toggle
│   └── img/                  ← put your own photos/videos here (empty for now)
└── README.md
```

Every page shares the same top nav bar (Home / Onboarding / Extrusion Floor /
Casthouse & HyForge / Handover / Gallery / Reflection) and the same
`assets/style.css`, so editing the stylesheet once updates the whole site.
There's no build step — it's plain HTML/CSS/JS, so it works on GitHub Pages
with zero configuration.

## 1. Put it in a GitHub repo

If you don't already have a repo:

```bash
cd path/to/this/folder
git init
git add .
git commit -m "Initial site"
```

Create a new repo on GitHub (via the web UI, "New repository"), then:

```bash
git remote add origin https://github.com/<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

## 2. Turn on GitHub Pages

1. On GitHub, go to your repo → **Settings** → **Pages**.
2. Under "Build and deployment", set **Source** to `Deploy from a branch`.
3. Set **Branch** to `main` and folder to `/ (root)`.
4. Save. GitHub will give you a URL like:
   `https://<your-username>.github.io/<repo-name>/`
   (takes a minute or two to go live after the first push.)

## 3. Adding your own photos/videos

- Drop image files into `assets/img/` (e.g. `assets/img/press-floor.jpg`).
- Replace a placeholder block like this:
  ```html
  <div class="media-slot"> ... dashed placeholder ... </div>
  ```
  with:
  ```html
  <div class="media-slot filled">
    <img src="../assets/img/press-floor.jpg" alt="Describe the photo">
  </div>
  ```
  (Note: from a file inside `phases/`, the path is `../assets/img/...`;
  from `index.html`, `gallery.html`, or `reflection.html` at the root, it's
  `assets/img/...`.)
- For your own video, either:
  - Upload it to YouTube (even "unlisted") and embed it the same way the
    existing videos are embedded (`<iframe src="https://www.youtube.com/embed/VIDEO_ID">`), or
  - Add an `.mp4` file to `assets/img/` and use:
    ```html
    <video controls src="../assets/img/my-clip.mp4"></video>
    ```

## 4. Editing content

Every page has `[bracketed placeholders]` for things only you know: dates,
your name, your role, specific tasks, and your own reflections. Search each
file for `[` to find them quickly.

## 5. Adding a new page

To add a fifth phase or another section:

1. Copy an existing file in `phases/` as a starting point.
2. Update its `<title>`, hero text, and content.
3. Add a link to it in the `.nav-links` list in **every** HTML file (so the
   nav bar stays consistent across the site) — or, if that gets tedious,
   consider moving to a static site generator like Jekyll (which GitHub
   Pages supports natively) so the nav lives in one shared layout file.

## Local preview

No server needed — just open `index.html` directly in a browser, or run a
quick local server from this folder:

```bash
python3 -m http.server 8000
```

then visit `http://localhost:8000`.
