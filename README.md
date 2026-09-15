# Yaghoub Rahimi academic website

A lightweight, static academic website for Yaghoub Rahimi, Postdoctoral Researcher in Mathematics at Louisiana State University. The layout is inspired by [Academic Pages](https://academicpages.github.io/): restrained typography, a left profile sidebar, simple navigation, and content-first publication and talk lists.

The site uses plain HTML and CSS. It has no build step, package manager, or Jekyll dependency.

## Site files

- `index.html` — biography, research interests, and recent news
- `research.html` — research themes
- `publications.html` — publications and preprints
- `talks.html` — selected talks in reverse chronological order
- `teaching.html` — courses and teaching roles
- `notes.html` — placeholder for future notes
- `cv.html` — CV downloads and PDF preview
- `contact.html` — LSU contact information and academic profiles
- `ams-2027.html` — special-session details and abstract for the AMS Spring 2027 Southeastern Sectional Meeting
- `404.html` — a helpful page for missing addresses on GitHub Pages
- `sitemap.xml` and `robots.txt` — public-page discovery for search engines
- `assets/styles.css` — site-wide design and responsive layout
- `assets/favicon.svg` — small YR icon for browser tabs
- `assets/og.jpg` — social-preview image used when the site is shared
- `assets/profile-placeholder.svg` — temporary profile image
- `assets/files/Yaghoub_Rahimi_CV.pdf` — downloadable CV
- `assets/files/Yaghoub_Rahimi_CV.tex` — CV LaTeX source

## Preview locally

From the repository root, run:

```bash
python3 -m http.server 8000 --bind 127.0.0.1
```

Then open `http://127.0.0.1:8000/`. Stop the server with `Ctrl+C`.

## Edit content

The navigation, sidebar, and footer are repeated in each HTML file so that the site remains build-free. When changing shared information such as the email address or job title, update all nine content pages, including the session page; keep the navigation on `404.html` in sync too. Searching the project for the old text is the safest way to find every copy. Update the affected pages' footer dates when reviewing their content, and add any new public page to `sitemap.xml`.

Unconfirmed content is marked with `TODO(content)` inside HTML comments. These comments are not visible on the published site.

After changing the shared CSS, update the `?v=...` value in every stylesheet link so returning visitors receive the new styling.

### Replace the profile photo

1. Add a square professional photograph at `assets/profile.jpg` (at least 500 × 500 pixels is recommended).
2. In every HTML file, replace:

   ```html
   src="assets/profile-placeholder.svg"
   ```

   with:

   ```html
   src="assets/profile.jpg"
   ```

3. Change the empty `alt=""` to a concise description if the photo conveys information not already supplied by the adjacent name.

### Replace the CV

Replace these files while keeping their filenames unchanged:

- `assets/files/Yaghoub_Rahimi_CV.pdf`
- `assets/files/Yaghoub_Rahimi_CV.tex`

Keeping the filenames preserves links from the homepage, sidebar, CV page, and contact page. If the LaTeX source changes, compile it before committing so the PDF and source stay synchronized.

With a LaTeX distribution installed, compile twice from the `assets/files/` folder:

```bash
pdflatex -no-shell-escape -interaction=nonstopmode -halt-on-error Yaghoub_Rahimi_CV.tex
pdflatex -no-shell-escape -interaction=nonstopmode -halt-on-error Yaghoub_Rahimi_CV.tex
```

Check the resulting PDF's page breaks and links, and update its explicit date and the date shown on `cv.html`. On phones, the CV page offers direct PDF links instead of a small embedded viewer.

### Add a publication

Add the newest item to the appropriate ordered list in `publications.html`. Use the title-first format:

```html
<li id="short-paper-name">
  <div class="publication-title">Paper title</div>
  <div class="authors">Coauthor One and <span class="me">Yaghoub Rahimi</span></div>
  <div class="venue"><em>Journal Name</em> volume, pages, year.</div>
  <div class="paper-links">
    <a href="ARXIV_URL">arXiv</a>
    <span class="link-separator" aria-hidden="true">·</span>
    <a href="JOURNAL_URL">Journal</a>
    <span class="link-separator" aria-hidden="true">·</span>
    <a href="PDF_URL">PDF</a>
  </div>
</li>
```

Announce a new paper at the top of the Recent news list in `index.html`, with the posting date, title, coauthors, and arXiv link. If it develops a research theme, update the relevant paragraph in `research.html` and link to the publication entry using its `id`.

Add the same citation to `assets/files/Yaghoub_Rahimi_CV.tex` and rebuild the PDF. Use “Preprint” unless a journal status has been confirmed.

### Update the AMS special session

Edit `ams-2027.html` for the session abstract and meeting details. Add co-organizers, speakers, and the schedule only once confirmed, and link to the public AMS session listing when it becomes available. Do not upload organizer emails, private access links, or unpublished submissions. Keep the homepage announcement brief and link it to this page.

### Add a talk

Add the newest talk to the top of the timeline in `talks.html`:

```html
<li>
  <time class="timeline-date" datetime="YYYY-MM-DD">Month D, YYYY</time>
  <div>
    <div class="timeline-title">Talk title</div>
    <div class="timeline-meta">Seminar or conference, institution.</div>
  </div>
</li>
```

Link the event name or slides only when a stable public URL is available.

## GitHub Pages deployment

This site is hosted from `Yaghoub-Rahimi/Yaghoub-Rahimi.github.io`. Review changes on a separate branch and merge the pull request when ready to publish. The existing Pages configuration deploys from the root of `main`; if configuring it again:

1. Open the repository on GitHub.
2. Select **Settings** → **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Select the `main` branch and the `/(root)` folder, then click **Save**.
5. Wait for the Pages deployment to finish. GitHub shows the deployment status and published URL on the same page.

The published URL is `https://yaghoub-rahimi.github.io/`. Canonical links, the sitemap, and the root-relative base in `404.html` are configured for this address. Update them if moving the site to a different domain or a project subdirectory.

The `.nojekyll` file tells GitHub Pages to serve this repository as plain static files. No GitHub Actions workflow is required for this site.
