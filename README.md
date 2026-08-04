# Yaghoub Rahimi academic website

A lightweight, static academic website for Yaghoub Rahimi, Postdoctoral Researcher in Mathematics at Louisiana State University. The layout is inspired by [Academic Pages](https://academicpages.github.io/): restrained typography, a left profile sidebar, simple navigation, and content-first publication and talk lists.

The site uses plain HTML and CSS. It has no build step, package manager, or Jekyll dependency.

## Site files

- `index.html` — biography, research interests, recent news, and selected publications
- `research.html` — research themes
- `publications.html` — publications and preprints
- `talks.html` — selected talks in reverse chronological order
- `teaching.html` — courses and teaching roles
- `notes.html` — placeholder for future notes
- `cv.html` — CV downloads and PDF preview
- `contact.html` — LSU contact information and academic profiles
- `assets/styles.css` — site-wide design and responsive layout
- `assets/og.png` — social-preview image used when the site is shared
- `assets/profile-placeholder.svg` — temporary profile image
- `assets/files/Yaghoub_Rahimi_CV.pdf` — downloadable CV
- `assets/files/Yaghoub_Rahimi_CV.tex` — CV LaTeX source

## Preview locally

From the repository root, run:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/`. Stop the server with `Ctrl+C`.

## Edit content

The navigation, sidebar, and footer are repeated in each HTML file so that the site remains build-free. When changing shared information such as the email address or job title, update all eight HTML pages. Searching the project for the old text is the safest way to find every copy.

Unconfirmed content is marked with `TODO(content)` inside HTML comments. These comments are not visible on the published site.

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

### Add a publication

Add the newest item to the appropriate ordered list in `publications.html`. Use the title-first format:

```html
<li>
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

If the paper should also be highlighted on the homepage, add a shorter version to the selected-publications list in `index.html`.

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

The preferred user-site repository is `yaghoub-rahimi.github.io` under the `Yaghoub-Rahimi` account. GitHub's documentation requires lowercase letters in the repository name for a user site. After this pull request is merged into `main`:

1. Open the repository on GitHub.
2. Select **Settings** → **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Select the `main` branch and the `/(root)` folder, then click **Save**.
5. Wait for the Pages deployment to finish. GitHub shows the deployment status and published URL on the same page.

For a repository named `yaghoub-rahimi.github.io`, the site URL is `https://yaghoub-rahimi.github.io/`. If the files are instead placed in a project repository, the default URL is `https://yaghoub-rahimi.github.io/REPOSITORY-NAME/`.

The `.nojekyll` file tells GitHub Pages to serve this repository as plain static files. No GitHub Actions workflow is required for this site.
