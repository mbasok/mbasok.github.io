# Mikhail Basok — personal website

A minimal four-page Quarto website for GitHub Pages.

The ZIP includes a rendered copy: open `_site/index.html` after extracting it to review the website immediately. Edit the `.qmd` source files rather than the generated HTML.

## Preview and build

Install [Quarto](https://quarto.org/docs/get-started/), then open a terminal in this folder:

```sh
quarto preview
```

To generate the site without starting a preview:

```sh
quarto render
```

The rendered files appear in `_site/`. No R, Python, Node.js, or additional packages are needed to build this site. The automated workflow uses Quarto 1.8.27.

## Publish on GitHub Pages

1. Create a public GitHub repository named `YOUR-USERNAME.github.io` for a site at `https://YOUR-USERNAME.github.io/`. You can instead use another repository name for a site at `https://YOUR-USERNAME.github.io/REPOSITORY/`.
2. Put the contents of this folder in the repository root, including `.github/workflows/publish.yml`. Use `main` as the default branch. Do not upload just the ZIP file or leave the project inside an extra nested folder.
3. Open the repository's **Settings → Pages** and choose **GitHub Actions** as the source.
4. Open **Actions → Publish Quarto website → Run workflow**. Subsequent commits to `main` will render and publish automatically.
5. The deployment job reports the website URL when it finishes successfully.

If using Git locally, after creating an empty repository:

```sh
git init -b main
git add .
git commit -m "Create personal Quarto website"
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

Replace the username and repository placeholders. If you already have a repository with content, integrate the files into it instead of initializing over it. Navigation uses relative links and works for either a user site or a project site.

After the public URL is known, you can add `site-url: https://YOUR-USERNAME.github.io/` under `website:` in `_quarto.yml` (include the repository path for a project site).

## Edit the content

| File | Content |
| --- | --- |
| `index.qmd` | Name, affiliation, research, selected works, profile links |
| `publications.qmd` | One chronological numbered list |
| `events.qmd` | Talks and conference organization |
| `teaching.qmd` | Teaching experience |
| `styles.css` | Typography, spacing, colours, responsive layout |
| `theme.scss` | Quarto theme defaults |
| `_quarto.yml` | Quarto configuration |

### Add your photograph

Save your photo as `images/portrait.jpg`. In `index.qmd`, replace the `portrait-placeholder` div with:

```html
<img class="portrait" src="images/portrait.jpg" alt="Mikhail Basok" width="148" height="176">
```

The reserved portrait area has a vertical crop. Adjust `object-position` in `styles.css` if necessary.

### Add a short description

Each selected work has a native HTML `<details>` section that opens through its “Short description” control and works without JavaScript. Replace:

```html
<p class="summary-placeholder">Description to be added.</p>
```

with your own paragraph, removing the placeholder class:

```html
<p>Your description here.</p>
```

For multiple paragraphs, add additional `<p>...</p>` elements. Quarto supports inline mathematics using `$...$` in ordinary Markdown content; for longer mathematical summaries, use Markdown inside the details element with blank lines around the content.

### Publications and dates

The list contains all 11 works returned by the arXiv author search on 22 September 2026, ordered newest to oldest by the year of the journal issue for published papers, and by first arXiv submission for preprints and forthcoming articles. Six published works have full journal citations and DOI links, with all arXiv links retained. The homology paper uses its 2024 journal issue year (it appeared online in 2023). The caustic paper uses the title and year of its English journal version. “Dimers on Riemann surfaces and compactified free field” is forthcoming in The Annals of Probability; no volume or pages have been assigned in the verified records. Published papers use their journal titles. The selected Tutte paper keeps the title supplied in the brief; arXiv's latest title reads “Harmonic functions on Tutte embeddings and linearized Monge-Ampère equation”.

The research statement has only light corrections: punctuation, “the theory of t-embeddings”, and “understanding SLE”. The teaching page retains your current-course statement and the relative “last four years” wording; update these as your teaching changes.

## Sources

- [arXiv author search, all archives](https://arxiv.org/search/?query=Basok%2C+M&searchtype=author): 11 works. Each item links to its arXiv record.
- [Helsinki research profile](https://researchportal.helsinki.fi/en/persons/mikhail-basok/): identity and cross-checks of publication records.
- [Published caustic paper](https://doi.org/10.1090/spmj/1672): later title.
- Events and teaching: supplied biography and links. The CIRM dates were checked against its conference page. Dates not supplied or verified have not been guessed.
- [Quarto GitHub Pages guide](https://quarto.org/docs/publishing/github-pages.html).
- [GitHub Pages custom workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).

Google Scholar did not permit retrieval during preparation. Its supplied profile link is included unchanged. The affiliation follows your supplied current Aalto affiliation.

## Validation

All four pages were rendered successfully using Quarto 1.8.27 with Pandoc 3.6.3 (the bundled Pandoc executable could not run in the preparation environment). The generated HTML was checked for one main heading per page, unique IDs, working local file references, five disclosure sections, and one publication list containing 11 entries. A browser-based visual and interaction check could not be completed because the browser download failed. The GitHub Actions deployment has not yet run; GitHub access and a target repository are still needed.


Journal references were checked against publisher records, with Helsinki research records as cross-checks. The DOI links on the Publications page identify the six journal versions. Forthcoming status was checked against the [Annals of Probability future-papers list](https://imstat.org/journals-and-publications/annals-of-probability/annals-of-probability-future-papers/) and the author's [Kenyon identities preprint](https://arxiv.org/abs/2511.03804).
